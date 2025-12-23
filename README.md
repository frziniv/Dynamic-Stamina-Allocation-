# Dynamic-Stamina-Allocation-
if not is_high_priority and self.current_stamina < (self.emergency_reserve + cost):
            print(f"[RESERVED] Action '{action_name}' blocked to save energy for Rank 1 moves.")
        else:
            print(f"[FAILED] Critical depletion! Cannot execute {action_name}.")
        return False

    def recover(self, delta_time: float):
        self.current_stamina = min(self.max_stamina, self.current_stamina + (self.regeneration_rate * delta_time))

# Example Usage
if __name__ == "__main__":
    sm = StaminaManager()
    # Spend stamina down to near the reserve
    sm.execute_action("Heavy_Attack", 70.0, is_high_priority=True) 
    
    # Try a low-priority move that would hit the reserve
    # This should be blocked by the new logic
    sm.execute_action("Casual_Dash", 10.0, is_high_priority=False)
# Example Usage
if __name__ == "__main__":
    sm = StaminaManager()
    sm.execute_action("Sprint", 30.0)
    sm.recover(5.0) # Recover for 5 seconds
