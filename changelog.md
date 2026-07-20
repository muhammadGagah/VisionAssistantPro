## Changes for 2026.07.15

*   **Intelligent API Model Filtering**: Complete overhaul of the model filtering system to use a pure blacklist approach instead of whitelists. Added stronger filtering keywords (`embedding`, `bison`, `gecko`, `audio`, `realtime`, `babbage`, `moderation`, `deep`, `antigravity`, `computer`) to ensure the main chat model dropdown remains perfectly clean and future-proof, while keeping all specialized models accessible in the Advanced Routing section.
*   **Advanced Routing Search**: All Advanced Model Routing dropdowns (OCR, STT, TTS, Operator, Video, Live) and the eSpeak Variant selector are now fully searchable. You can quickly type to filter and find your desired model or variant.
*   **New Command Layer Shortcuts**:
    *   **Settings (`Alt + S`)**: Instantly opens the Vision Assistant Pro settings dialog.
    *   **Quota Exhausted Keys Report (`Alt + Q`)**: Reports the exact number of Gemini API keys that have exceeded their daily quota, identifying which specific model they are exhausted on, and announces their exact reset time.
    *   **Routing Audit (`Alt + M`)**: Audits and announces your current Advanced Routing configuration, reading out which models are actively selected for specialized tasks (skipping default settings).
*   **Video Analyzer Complete Overhaul**: The Video Analyzer has been completely transformed! Previously, it only provided a basic description of online videos. Now, it is a comprehensive video processing suite tailored for blind users:
    *   **Local Screen Recording (`Control+V`)**: You can now record silent videos directly from your screen. The AI will analyze the recorded segment and provide a highly detailed description of the scene, layout, and actions.
    *   **Audio Description Generation (SRT)**: The add-on can now generate highly detailed Audio Description scripts (in standard SRT format) for videos, complete with smart gap-timing to intelligently anchor descriptions to natural pauses in the audio track, and verbatim OCR for any on-screen text.
    *   **Synchronized Audio Narration (MP3 Export)**: Beyond text-based subtitles, the add-on can synthesize the Audio Description into speech, automatically mix it with the video's original audio track, apply audio ducking (lowering background volume during descriptions), and export the final synchronized result as an MP3 file!
    *   **Smart Video File Action**: If you focus on a local video file and press the video shortcut, the add-on will automatically detect it and process the file directly.
    *   **Advanced Character Tracking**: The AI now performs a character extraction pre-pass. It builds a global character dictionary and tracks characters accurately segment-by-segment without confusing identities.
    *   **Video Analysis Configuration**: Added new settings to control SRT chunk sizes, character subtitling, and disclaimers.
    *   **Extended Model Routing**: You can now explicitly select specialized video models (`gemini_video_model`, `custom_video_model`) in the Advanced Model Routing settings.
*   **Smart API Quota Management**: Enhanced handling of 429 (Daily Limit) errors by tracking quotas per-model. If a key hits its daily limit on one model, it is intelligently quarantined for that specific model only, leaving the key available for use with other models.

---

### 🌟 Support the Future of Vision Assistant Pro

Vision Assistant Pro is a mission to bridge the gap between AI and true accessibility. Maintaining and testing a cloud-based AI tool under internet restrictions is a constant battle. 

Each major testing cycle of our new visual features consumes active API credits (often costing $10+ per test run out of my own pocket), in addition to high local infrastructure costs.

As an open-source project, Vision Assistant Pro thrives on community support. If you'd like to help cover these ongoing development and testing costs, please consider supporting the project:

* 🍎 **Apple US Gift Cards:** Please send the gift card code to: `visionassistantpro@proton.me` (You can purchase them globally here: [Buy Apple US Gift Cards](https://www.mygiftcardsupply.com/shop/itunes-gift-cards/))
* 💎 **Cryptocurrency (TON):** `UQDoOOOoDYPP8eqWXVsjVyYzulY72JLZK1grPS_O2DbgVNsc`

Thank you for being part of this journey!