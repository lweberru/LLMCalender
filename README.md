# 🗓️ Home Assistant Blueprint – Fetch Calendar Events

This project provides a **Home Assistant Blueprint** that allows you to query events from one or more calendar entities.  
The blueprint is especially useful for **LLMs / Assistive Tools**, since it returns structured data in a predictable format.

---

## 🚀 Features

- Query **multiple calendars** at once  
- Define a custom time span (`start_of_period`, `end_of_period`)  
- Returns results as a **dictionary** with all events  
- Each event includes:
  - `calendar` (source entity)  
  - `start` (start datetime)  
  - `end` (end datetime)  
  - `summary` (event title)  
  - `location` (optional, if available)  

Example result:

```yaml
response:
  start_of_period: "2025-10-01T00:00:00+02:00"
  end_of_period: "2025-10-31T00:00:00+02:00"
  events:
    - calendar: calendar.badminton_gemmrigheim
      start: "2025-10-11T14:00:00+02:00"
      end: "2025-10-11T16:00:00+02:00"
      summary: "Badminton: SG Gemmrigheim/Neckarwestheim vs. TV Tamm II"
      location: "Wasenhalle Gemmrigheim, Mühläckerweg, 74376 Gemmrigheim"
    - calendar: calendar.mull
      start: "2025-10-08"
      end: "2025-10-09"
      summary: "Restmuelltonne"
```

---

## 📥 Installation

1. Open Home Assistant → **Settings → Automations & Scenes → Blueprints**  
2. Click the three-dot menu in the top right → **Import Blueprint**  
3. Enter this GitHub URL:

   ```
   https://github.com/<YOUR_GITHUB_REPO>/blob/main/fetch_calendar_events.yaml
   ```

4. The blueprint will now be available in your Home Assistant instance.  

---

## ⚙️ Usage

1. Go to **Scripts** and create a new script based on this blueprint.  
2. Configure the inputs:
   - **Calendars** → select one or more calendar entities to query  
   - **Start of period** → ISO datetime string  
   - **End of period** → ISO datetime string  

3. Run the script → the results will be returned via the `response_variable` and can be consumed by automations, assistants, or LLM integrations.  

---

## 🤖 Using with Assistants

To make this script available for use with Assistants in Home Assistant:  

1. Open the created script in **Scripts**.  
2. Go to **Settings** of the script and enable **Expose to Assistants**.  
   - This makes the script callable via voice or chat assistants.  

### Example phrase

Once exposed, you can ask your assistant:  

```
Show me all badminton events for this October
```

The assistant will then call the script, retrieve the events, and respond with the results.  

---

## 🔄 Updating the Blueprint

If you update the blueprint on GitHub, Home Assistant does **not** automatically reload it. You need to:

- Go to **Settings → Blueprints → Three-dot menu → Re-import Blueprint**,  
  and provide the same GitHub URL again, **or**  
- Replace the YAML file manually in `/config/blueprints/script/` and reload blueprints from the **Developer Tools → YAML → Reload Scripts & Blueprints**.  

---

## 📝 License

This project is licensed under the MIT License.  

---

✨ Enjoy using and extending this blueprint!
