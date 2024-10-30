# Task3
import re

def assess_password_strength(password):
    score = 0
    feedback = []

    # Check for length
    if len(password) >= 8:
        score += 1
    else:
        feedback.append("Password should be at least 8 characters long.")

    # Check for uppercase letters
    if re.search(r"[A-Z]", password):
        score += 1
    else:
        feedback.append("Password should include at least one uppercase letter.")

    # Check for lowercase letters
    if re.search(r"[a-z]", password):
        score += 1
    else:
        feedback.append("Password should include at least one lowercase letter.")

    # Check for digits
    if re.search(r"\d", password):
        score += 1
    else:
        feedback.append("Password should include at least one digit.")

    # Check for special characters
    if re.search(r"[!@#$%^&*(),.?\":{}|<>]", password):
        score += 1
    else:
        feedback.append("Password should include at least one special character (!@#$%^&*(),.?\":{}|<>).")

    # Assess strength based on score
    if score == 5:
        strength = "Very Strong"
    elif score == 4:
        strength = "Strong"
    elif score == 3:
        strength = "Moderate"
    elif score == 2:
        strength = "Weak"
    else:
        strength = "Very Weak"

    return strength, feedback

# User input
password = input("Enter a password to assess its strength: ")

# Get strength and feedback
strength, feedback = assess_password_strength(password)

# Display result
print(f"Password Strength: {strength}")
if feedback:
    print("Suggestions to improve your password:")
    for suggestion in feedback:
        print(f" - {suggestion}")
