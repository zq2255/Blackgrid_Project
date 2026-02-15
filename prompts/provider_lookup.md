You are helping me build a prototype for “Provider lookup” for a master’s project.

Goal
- Implement a Python function that searches for healthcare providers using Google Maps/Places API and returns structured provider contact info, especially phone numbers.
- IMPORTANT: Never invent phone numbers. Phone must come from Google Places data.

Inputs
- provider_scope (REQUIRED): one of ["urgent care", "emergency room", "pharmacy", "radiology center"] (but should accept any string)
- zip_code (OPTIONAL): string like "10027". If missing, default to "10027" for testing.
- radius_meters (OPTIONAL): default 5000.
- max_results (OPTIONAL): default 10.
- api_key: read from environment variable GOOGLE_MAPS_API_KEY (do NOT hardcode).

Requirements
1) Use Google Places search (Text Search or Nearby Search) to find candidate providers given provider_scope + zip_code (+ radius).
2) For each candidate, fetch phone number by calling Place Details API (because search results may not include formatted_phone_number).
3) Return a list of dictionaries with exactly these keys:
   - name
   - phone (formatted_phone_number if available, otherwise empty string)
   - address (formatted_address or vicinity)
   - place_id
   - lat
   - lng
4) Handle missing phone gracefully (leave phone="").
5) Include basic error handling:
   - If API key missing, raise a clear error.
   - If Google API returns no results, return [].
6) Provide a small runnable example in a __main__ block:
   - scope="urgent care", zip_code="10027"
   - Print the first 3 results nicely.
7) Keep the code in a single file called provider_lookup.py.
8) Also include a short comment at the top explaining: “We rely on Places for phone numbers to avoid LLM hallucination.”

Notes
- Use the simplest dependency approach: requests + urllib.parse (preferred), OR googlemaps library if you think it is cleaner. Either is fine, but keep it easy to run.
- Keep it prototype-quality but clean and readable.

Deliverable
- Output provider_lookup.py content only.

