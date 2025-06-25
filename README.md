# SCBX-and-AIAT-FinHackathon-2025

### Model Testing Experiment

We experimented with 2 models: typhoon-v2-70b-instruct and deepseek-chat-v3.

### Initial Testing with Typhoon-v2-70b-instruct

When using typhoon-v2-70b-instruct, the Standard Prompt score was not much lower than Chain-of-Thought. When we tried adjusting some parts of the prompt, the score didn't change much.

### Switch to DeepSeek-Chat-v3

We switched to deepseek-chat-v3 instead, which gave much higher scores than before.

### Speed Optimization

We also focused on speed because we didn't want to wait too long for testing. We modified the question format before sending to the model by sending multiple questions at once to get as many as the token limit allows.

### New Question Format

```
id: 36deab86-cfd3-48b5-9bea-a36c1b0e63a8
"ตอบคำถามด้วยตัวเลือกที่เหมาะสม A, B, C และ D โปรดตอบด้วยคำตอบที่ถูกต้อง A, B, C หรือ D เท่านั้น อย่าใช้คำฟุ่มเฟือยหรือให้ข้อมูลเพิ่มเติม
คำถาม: ______ สถานที่ทำงานเกี่ยวข้องกับการเสริมสร้างศักยภาพให้พนักงาน ตัวอย่างเช่น 'job enrichment' ที่พนักงานได้รับขอบเขตที่ใหญ่ขึ้นในการตัดสินใจว่าจะจัดระเบียบงานของตนอย่างไร หรือ 'job enlargement' ที่พนักงานได้รับมอบหมายงานที่หลากหลายมากขึ้น
ตัวเลือกคำตอบ: A: Re-invigorating, B: Re-flourishing, C: Revitalizing, D: Rehumanizing
คำตอบ:"
```

### Additional Optimizations

We removed Answer Conditions from the questions to save tokens and made the output format as `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx,<answer>` to make it easy for Python to parse, since we ask as many questions as possible per model call within the token limit.
