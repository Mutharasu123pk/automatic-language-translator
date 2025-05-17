# automatic-language-translator
from googletrans import Translator, LANGUAGES

def automatic_translator():
    # Initialize translator
    translator = Translator()

    # Supported languages for this example
    supported_langs = {
        '1': 'en',  # English
        '2': 'es',  # Spanish
        '3': 'fr'   # French
    }

    print("Automatic Language Translator (3 Languages)")
    print("Supported languages:")
    print("1. English")
    print("2. Spanish")
    print("3. French")
    print()

    while True:
        try:
            # Get source language
            src_choice = input("Enter source language number (1-3) or 'q' to quit: ")
            if src_choice.lower() == 'q':
                break

            if src_choice not in supported_langs:
                print("Invalid choice. Please select 1, 2, or 3.")
                continue

            src_lang = supported_langs[src_choice]

            # Get target language
            dest_choice = input("Enter target language number (1-3): ")
            if dest_choice not in supported_langs:
                print("Invalid choice. Please select 1, 2, or 3.")
                continue

            dest_lang = supported_langs[dest_choice]

            # Get text to translate
            text = input(f"Enter text to translate from {LANGUAGES[src_lang]} to {LANGUAGES[dest_lang]}: ")

            # Perform translation
            translation = translator.translate(text, src=src_lang, dest=dest_lang)

            # Display results
            print("\nTranslation Results:")
            print(f"Original ({LANGUAGES[src_lang]}): {text}")
            print(f"Translated ({LANGUAGES[dest_lang]}): {translation.text}")
            print(f"Pronunciation: {translation.pronunciation if translation.pronunciation else 'Not available'}")
            print("-" * 50 + "\n")

        except Exception as e:
            print(f"An error occurred: {e}")
if __name__ == "__main__":
    automatic_translator()
