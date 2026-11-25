TryHackMe: Overhead at Breakfast (OSINT Challenge)

Category: OSINT, social media, hashing

Difficulty: Easy

Date: November 2026

OBJECTIVE:

The goal of this challenge was to analyze a provided conversation screenshot, extract relevant OSINT clues, find a hidden social media account, and decode the final flag.

TOOLS AND TECHNIQUES I USED:

· OSINT Analysis: reading the provided image (conversation.png) to extract indicators.

· Hashing: converting an email address to a hash.

· Gravatar: using the MD5 hash to look up a profile picture on Gravatar's database.

· Linux Terminal (Base64 decoding): decoding the final prize string.

STEP-BY-STEP WALKTHROUGH:

1. Analyzing the conversation

I downloaded the task files and opened conversation.png. While reading the dialogue, I found a crucial piece of information. Lambo mentioned he doesn't use social media much but left his email address for contact:
lambobyteLotushotel@gmail.com

2. Finding the Gravatar profile

Gravatar uses MD5 hashes of email addresses to link users to their profile pictures across different websites. So I took Lambo's email and converted it into an MD5 hash. Then, I appended this hash to the Gravatar URL format:
https://gravatar.com/d4a5fc5d3128890778667e24617d7cc0

3. Getting the Flag

The Gravatar profile loaded successfully and showed Lambo's profile. The bio contained a strange string: VEhNe1MzY3JWRF9QcjBmaWwzX0g0c19iMzNuX0lkZW50MWZpM2Q?

I recognized this format as Base64 encoding (indicated by the mix of uppercase, lowercase, numbers, and the = or ? at the end). I opened my Linux terminal and used the base64 command to decode it:
echo "VEhNe1MzY3JWRF9QcjBmaWwzX0g0c19iMzNuX0lkZW50MWZpM2Q?" | base64 -d

Flag: THM{S3crwd_Pr0fil3_H4s_b33n_Ident1fi3d}
