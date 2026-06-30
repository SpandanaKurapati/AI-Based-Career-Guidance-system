import streamlit as st

st.set_page_config(page_title="AI Career Guidance System", layout="centered")

# Title
st.title("🎓 AI-Powered Career Guidance System")
st.write("Smart career suggestions based on your interests and academic profile.")

# Collect Input
name = st.text_input("Your Name")
math = st.slider("Marks in Mathematics", 0, 100, 70)
science = st.slider("Marks in Science", 0, 100, 70)
english = st.slider("Marks in English", 0, 100, 70)

interest = st.selectbox(
    "Your Area of Interest",
    [
        "Technology",
        "Biology",
        "Business",
        "Arts",
        "Teaching",
        "Environment",
        "Law",
        "Media and Communication",
        "Psychology and Mental Health",
        "Finance and Accounting",
        "Social Work and Volunteering",
        "Travel and Tourism",
        "Gaming and Animation",
        "Sports and Fitness",
        "Fashion and Beauty",
        "Literature and Writing"
    ]
)

skills = st.multiselect(
    "Select Your Skills",
    [
        "Programming",
        "Designing",
        "Public Speaking",
        "Critical Thinking",
        "Data Analysis",
        "Writing",
        "Creativity",
        "Team Leadership",
        "Counseling",
        "Fitness Training"
    ]
)

hobby = st.selectbox(
    "What's Your Favorite Hobby?",
    [
        "Reading", "Coding", "Drawing", "Debating", "Nature Walks",
        "Fitness & Sports", "Traveling", "Blogging", "Photography", "Fashion Styling"
    ]
)

# AI Logic for Career Suggestion
def suggest_career(math, science, english, interest, skills):
    if interest == "Technology" and "Programming" in skills:
        return "👩‍💻 Software Developer / AI Engineer"
    elif interest == "Biology" and science > 80:
        return "🧬 Doctor / Biotechnologist"
    elif interest == "Business" and "Critical Thinking" in skills:
        return "📊 Business Analyst / Entrepreneur"
    elif interest == "Arts" and "Designing" in skills:
        return "🎨 Graphic Designer / UI-UX Designer"
    elif interest == "Teaching" and "Public Speaking" in skills:
        return "👩‍🏫 Teacher / Lecturer"
    elif interest == "Environment" and science > 75:
        return "🌱 Environmental Scientist"
    elif interest == "Law":
        return "⚖️ Lawyer / Legal Advisor"
    elif interest == "Media and Communication" and "Public Speaking" in skills:
        return "📰 Journalist / Media Strategist"
    elif interest == "Psychology and Mental Health" and "Counseling" in skills:
        return "🧠 Psychologist "
    elif interest == "Finance and Accounting" and "Data Analysis" in skills:
        return "💰 Financial Analyst / Chartered Accountant"
    elif interest == "Social Work and Volunteering":
        return "🤝 Social Worker / NGO Leader"
    elif interest == "Travel and Tourism":
        return "✈️ Travel Consultant / Tour Guide / Blogger"
    elif interest == "Gaming and Animation" and "Designing" in skills:
        return "🎮 Game Developer / Animator / VFX Artist"
    elif interest == "Sports and Fitness" and "Fitness Training" in skills:
        return "🏋️ Fitness Trainer / Physiotherapist"
    elif interest == "Fashion and Beauty" and "Creativity" in skills:
        return "👗 Fashion Designer / Stylist"
    elif interest == "Literature and Writing" and "Writing" in skills:
        return "📚 Author / Content Writer / Editor"
    else:
        return "🔍 Career Counselor Guidance Recommended"

# Display Result
if st.button("Get Career Suggestion"):
    career = suggest_career(math, science, english, interest, skills)
    user_name = name if name.strip() else "User"
    st.success(f"Hi {user_name}, based on your profile, we suggest: \n\n**{career}**")

    st.markdown("---")
    st.info("📚 Tip: Consider exploring online courses, workshops, and internships related to this career path.")
