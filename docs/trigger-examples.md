# ASPT Checkpoint Trigger Examples

This document provides implementation examples for each type of checkpoint trigger in the ASPT methodology.

## 1. Component Completion Trigger

This trigger initiates a review after completing a functional unit such as a class or method.

```python
# Orchestration layer implementation example
class ComponentCompletionTrigger:
    def __init__(self, code_analyzer):
        self.code_analyzer = code_analyzer
        self.last_component_count = 0
    
    def check(self, code_state):
        """Check if a new component has been completed."""
        current_components = self.code_analyzer.count_components(code_state.code)
        if current_components > self.last_component_count:
            self.last_component_count = current_components
            return True
        return False
```

**Prompt-based implementation:**
```
When you have completed implementing a class, method, or function, 
immediately perform a Shallow Stitch review on that component before 
proceeding to implement any dependent components.
```

## 2. Line Count Trigger

This trigger initiates a review after generating a specific number of lines of code.

```python
# Orchestration layer implementation example
class LineCountTrigger:
    def __init__(self, threshold=50):
        self.threshold = threshold
        self.last_review_line = 0
    
    def check(self, code_state):
        """Check if line count threshold has been reached since last review."""
        current_line_count = code_state.line_count
        if current_line_count - self.last_review_line >= self.threshold:
            self.last_review_line = current_line_count
            return True
        return False
```

**Prompt-based implementation:**
```
After generating every 50 lines of code, pause and perform a Shallow Stitch 
review on the most recently written section before continuing.
```

## 3. Complexity Threshold Trigger

This trigger initiates a review after implementing complex logic such as nested conditionals.

```python
# Orchestration layer implementation example
class ComplexityThresholdTrigger:
    def __init__(self, complexity_analyzer, threshold=10):
        self.complexity_analyzer = complexity_analyzer
        self.threshold = threshold
        self.reviewed_sections = set()
    
    def check(self, code_state):
        """Check if any section exceeds complexity threshold."""
        complex_sections = self.complexity_analyzer.find_complex_sections(
            code_state.code, self.threshold
        )
        
        # Find sections that exceed threshold and haven't been reviewed
        new_complex_sections = [
            section for section in complex_sections 
            if section.id not in self.reviewed_sections
        ]
        
        if new_complex_sections:
            # Mark these sections as reviewed
            for section in new_complex_sections:
                self.reviewed_sections.add(section.id)
            return True
        
        return False
```

**Prompt-based implementation:**
```
After implementing any logic with:
- Nested conditionals deeper than 2 levels
- Multiple exception handling blocks
- Complex regular expressions
- Recursive functions

Immediately perform a Shallow Stitch review focused on logical correctness
and edge case handling.
```

## 4. Integration Point Trigger

This trigger initiates a review before connecting to dependent components.

```python
# Orchestration layer implementation example
class IntegrationPointTrigger:
    def __init__(self, dependency_analyzer):
        self.dependency_analyzer = dependency_analyzer
        self.integration_points_reviewed = set()
    
    def check(self, code_state):
        """Check if new integration points are being implemented."""
        integration_points = self.dependency_analyzer.find_integration_points(code_state.code)
        
        # Find integration points that haven't been reviewed
        new_integration_points = [
            point for point in integration_points 
            if point.id not in self.integration_points_reviewed
        ]
        
        if new_integration_points:
            # Mark these integration points as reviewed
            for point in new_integration_points:
                self.integration_points_reviewed.add(point.id)
            return True
        
        return False
```

**Prompt-based implementation:**
```
Before implementing any code that:
- Calls an external API
- Integrates with another component you've written
- Uses third-party libraries
- Accesses shared resources (database, file system, etc.)

Perform a Medium Stitch review on the component that will be doing the integration.
```

## 5. Time-Based Trigger

This trigger initiates a review after a set duration of continuous generation.

```python
# Orchestration layer implementation example
class TimeBasedTrigger:
    def __init__(self, interval_minutes=15):
        self.interval_seconds = interval_minutes * 60
        self.last_review_time = time.time()
    
    def check(self, code_state):
        """Check if time interval has elapsed since last review."""
        current_time = time.time()
        if current_time - self.last_review_time >= self.interval_seconds:
            self.last_review_time = current_time
            return True
        return False
```

**Prompt-based implementation:**
```
After every 15 minutes of continuous code generation, pause and perform
a Shallow Stitch review on all code written since the last review.
```

## 6. User-Initiated Trigger

This trigger initiates a review when explicitly requested by the user.

```python
# Orchestration layer implementation example
class UserInitiatedTrigger:
    def __init__(self):
        self.review_requested = False
    
    def request_review(self):
        """User interface calls this to request a review."""
        self.review_requested = True
    
    def check(self, code_state):
        """Check if user has requested a review."""
        if self.review_requested:
            self.review_requested = False  # Reset the flag
            return True
        return False
```

**Prompt-based implementation:**
```
When I say "REVIEW", pause your code generation and perform a 
Shallow Stitch review on the most recently written section.

When I say "MEDIUM REVIEW", perform a Medium Stitch review on the 
entire component you're currently working on.

When I say "DEEP REVIEW", perform a Deep Stitch review on the entire
system as it currently stands.
```

## 7. Composite Trigger

In practice, multiple triggers are often combined in an orchestration layer.

```python
# Orchestration layer implementation example
class CompositeTrigger:
    def __init__(self, triggers):
        self.triggers = triggers
    
    def check(self, code_state):
        """Check all triggers and return True if any trigger is activated."""
        return any(trigger.check(code_state) for trigger in self.triggers)
```

**Prompt-based implementation:**
```
As you generate code, continuously monitor for the following review triggers:

1. After completing any function, class, or method
2. After every 50 lines of code
3. After implementing complex logic (nested conditionals, error handling)
4. Before integrating with other components
5. After 10 minutes of continuous generation
6. When I explicitly request a review

When any of these conditions are met, pause and perform the appropriate
level of review before continuing.
```

[Back to Specification](specification.md)
