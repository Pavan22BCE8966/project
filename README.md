# project


pip install openai


import openai

# Replace with your OpenAI API key
openai.api_key = "YOUR_API_KEY"

def generate_horror_story(setting, protagonist, fear_type, twist=True):
    prompt = f"""
    Write a horror story based on the following inputs:
    - Setting: {setting}
    - Protagonist: {protagonist}
    - Type of fear: {fear_type}
    - Include a twist ending: {"Yes" if twist else "No"}

    The story should be eerie, suspenseful, and highly atmospheric. Keep the reader on edge.
    Begin now:
    """

    response = openai.ChatCompletion.create(
        model="gpt-4",
        messages=[
            {"role": "system", "content": "You are a horror story writer."},
            {"role": "user", "content": prompt}
        ],
        temperature=0.9,
        max_tokens=800
    )

    story = response['choices'][0]['message']['content']
    return story

# Example usage
if __name__ == "__main__":
    setting = "abandoned mental asylum during a thunderstorm"
    protagonist = "a lone paranormal investigator named Clara"
    fear_type = "psychological and supernatural"

    story = generate_horror_story(setting, protagonist, fear_type)
    print("\n📖 Generated Horror Story:\n")
    print(story)
