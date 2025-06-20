#Mad libs (program-1)
def mad_libs(input_filename, output_filename):
    # Read the original text file
    with open(input_filename, 'r') as file:
        text = file.read(
    placeholders = ['ADJECTIVE', 'NOUN', 'ADVERB', 'VERB']
    words = text.split()
    for i in range(len(words)):
        stripped_word = words[i].strip('.,!?;:')
        if stripped_word in placeholders:
            article = 'an' if stripped_word[0] in 'AEIOU' else 'a'
            user_input = input(f"Enter {article} {stripped_word.lower()}: ")
            words[i] = words[i].replace(stripped_word, user_input)
    completed_text = ' '.join(words)
    print("\n--- Completed Mad Libs Story ---")
    print(completed_text)
    with open(output_filename, 'w') as file:
        file.write(completed_text)
    print(f"\nThe completed story has been saved to '{output_filename}'.")
if __name__ == "__main__":
    input_file = "madlibs_input.txt"  # Replace with your input file name
    output_file = "madlibs_output.txt"  # Output file name
    mad_libs(input_file, output_file)

