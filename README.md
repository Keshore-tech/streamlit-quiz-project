import streamlit as st

st.title("📝 Simple Quiz")

questions = [
    {
        "question": "What is the capital of France?",
        "options": ["Berlin", "Madrid", "Paris", "Rome"],
        "answer": "Paris"
    },
    {
        "question": "Which planet is known as the Red Planet?",
        "options": ["Earth", "Mars", "Jupiter", "Saturn"],
        "answer": "Mars"
    },
    {
        "question": "What is 10 + 15?",
        "options": ["20", "25", "30", "35"],
        "answer": "25"
    }
]

score = 0
user_answers = []

for i, q in enumerate(questions):
    st.write(f"**Q{i+1}. {q['question']}**")
    choice = st.radio(
        label="Select an option:",
        options=q["options"],
        key=i,
        label_visibility="collapsed"  # hides label but avoids warnings
    )
    user_answers.append(choice)

if st.button("Submit"):
    for user_ans, q in zip(user_answers, questions):
        if user_ans == q["answer"]:
            score += 1
    st.write(f"### Your Score: {score} / {len(questions)}")
