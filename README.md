# Dynamic-Stamina-Allocation-
# StaminaManager.py

class StaminaManager:
    def __init__(self, max_stamina: float = 100.0):
        self.max_stamina = max_stamina
        self.current_stamina = max_stamina
        self.regeneration_rate = 2.0  # Points per second

    def can_perform_action(self, cost: float) -> bool:
        """Checks if the agent has enough stamina for a specific action."""
        return self.current_stamina >= cost

    def execute_action(self, action_name: str, cost: float):
        """Consumes stamina if available."""
        if self.can_perform_action(cost):
            self.current_stamina -= cost
            print(f"[ACTION] {action_name} executed. Remaining Stamina: {self.current_stamina:.1f}")
            return True
        print(f"[FAILED] Not enough stamina for {action_name}.")
        return False

    def recover(self, delta_time: float):
        """Regenerates stamina based on time elapsed."""
        self.current_stamina = min(self.max_stamina, self.current_stamina + (self.regeneration_rate * delta_time))

# Example Usage
if __name__ == "__main__":
    sm = StaminaManager()
    sm.execute_action("Sprint", 30.0)
    sm.recover(5.0) # Recover for 5 seconds
