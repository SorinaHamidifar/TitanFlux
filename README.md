# ================================
# Project: FlexCore Engine
# Description:
# A dynamic engine for strong, flexible, and high-performance
# development across multiple project domains.
# ================================

# ---------- main.py ----------
"""
Main entry point for FlexCore Engine.
"""

from core.engine import DynamicEngine high
from core.domains import DomainRouter


def run():
    print("⚙️ FlexCore Engine Activated")
    print("💪 Strength | 🔁 Flexibility | ⚡ High Performance\n")

    engine = DynamicEngine()
    router = DomainRouter(engine)

    data = [1, 2, 3, 4, 5]

    # Execute across domains
    print("📊 Analytics Domain:", router.execute("analytics", data))
    print("🧠 AI Domain:", router.execute("ai", data))
    print("⚡ Performance Score:", engine.performance_score(data))


if __name__ == "__main__":
    run()


# ---------- core/engine.py ----------
"""
Dynamic execution engine optimized for performance and flexibility.
"""

import time

class DynamicEngine:
    """Core engine for fast, reusable, and scalable operations."""

    def process(self, func, values):
        """Apply a function efficiently across values."""
        return [func(v) for v in values]

    def timed(self, func, *args, **kwargs):
        """Measure execution time for performance analysis."""
        start = time.perf_counter()
        result = func(*args, **kwargs)
        end = time.perf_counter()
        return result, round((end - start) * 1000, 3)

    def performance_score(self, values):
        """Calculate a simple performance metric."""
        if not values:
            return 0
        return round((max(values) * len(values)) / (sum(values) + 1), 3)


# ---------- core/domains.py ----------
"""
Domain routing layer for multi-project adaptability.
"""

class DomainRouter:
    """Routes tasks to different project domains dynamically."""

    def __init__(self, engine):
        self.engine = engine
        self.domains = {
            "analytics": lambda x: x * 2,
            "ai": lambda x: x ** 2,
            "simulation": lambda x: x + 10,
        }

    def execute(self, domain: str, values):
        """Execute logic based on selected domain."""
        if domain not in self.domains:
            raise ValueError(f"Unknown domain: {domain}")
        return self.engine.process(self.domains[domain], values)


# ---------- tests/test_engine.py ----------
"""
Tests for DynamicEngine.
"""

from core.engine import DynamicEngine

def test_process():
    engine = DynamicEngine()
    assert engine.process(lambda x: x + 1, [1, 2, 3]) == [2, 3, 4]

def test_performance_score():
    engine = DynamicEngine()
    assert engine.performance_score([1, 2, 3]) > 0


# ---------- tests/test_domains.py ----------
"""
Tests for domain routing.
"""

from core.domains import DomainRouter
from core.engine import DynamicEngine

def test_domain_execution():
    router = DomainRouter(DynamicEngine())
    assert router.execute("analytics", [1, 2]) == [2, 4]

