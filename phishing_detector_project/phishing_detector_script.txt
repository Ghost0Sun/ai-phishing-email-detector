import re

def is_phishing_email(email_content):
    # Simple rules (AI-like patterns)
    red_flags = [
        "urgent", "act now", "verify your account",
        "click here", "login immediately", "update payment",
        "free gift", "account suspended", "suspicious activity",
        "confirm your identity", "you have won"
    ]

    # Count red flags
    score = 0
    for flag in red_flags:
        if re.search(flag, email_content, re.IGNORECASE):
            score += 1

    if score >= 3:
        return "🚨 Phishing email detected!"
    elif score == 2:
        return "⚠️ Suspicious email. Be careful."
    else:
        return "✅ Looks safe, but stay alert."

# Example usage
email = input("Paste the email content here:\n")
print(is_phishing_email(email))