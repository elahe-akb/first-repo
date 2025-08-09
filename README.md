# first-repo
test
# quote_fetcher.py
import requests

def fetch_random_quote():
    url = "https://api.quotable.io/random"
    response = requests.get(url)
    if response.status_code == 200:
        data = response.json()
        return data["content"], data["author"]
    else:
        raise Exception("Error fetching quote from API")

def analyze_text(text):
    words = text.split()
    return len(words), len(text)

if __name__ == "__main__":
    try:
        quote, author = fetch_random_quote()
        word_count, char_count = analyze_text(quote)

        print("📜 Quote:")
        print(f"“{quote}” — {author}")
        print("\n📊 Text Analysis:")
        print(f"Word count: {word_count}")
        print(f"Character count: {char_count}")
    except Exception as e:
        print("❌ Error:", e)
