# Wayfold – Hotel Booking App

A responsive hotel booking frontend: **Home → Search → Hotel Details → Booking → Confirmation**. It runs on mock data out of the box and is prepared for Supabase.

## Tech stack
React 18, Vite, React Router, plain CSS, Supabase (optional).

## Install and run
```
npm install
npm run dev     # open the printed http://localhost:5173 URL
npm run build   # production build
```
Requires Node.js 18 or newer.

## Structure
```
src/
  components/  Navbar, SearchBar, HotelCard, HotelImage, BookingForm, BookingSummary
  pages/       Home, Search, HotelDetails, Booking, Confirmation
  hooks/       useBooking.jsx (search criteria + latest booking, via context)
  utils/       booking.js (validation, pricing, reference generation, filtering)
  services/    supabaseClient.js, hotelService.js, bookingService.js
  data/        hotels.js (mock data, same shape as the hotels table)
supabase/      supabase.sql, seed.sql, README.md
.env.example
```
UI components never call Supabase. Pages call `hotelService` / `bookingService`, which use Supabase when configured and mock data otherwise.

## Supabase setup
1. Create a Supabase project.
2. Copy `.env.example` to `.env` and add your URL and anon key.
3. Run `supabase/supabase.sql` in the SQL Editor.
4. Run `supabase/seed.sql`.
5. Restart `npm run dev`.

See `supabase/README.md` for the security notes.

## Environment variables
| Name | Purpose |
|---|---|
| `VITE_SUPABASE_URL` | Supabase project URL |
| `VITE_SUPABASE_ANON_KEY` | Supabase public anon key |

## Booking flow
Home → Search → Hotel Details → Booking → Confirmation. Dates and guests are kept between pages, and the booking reference looks like `HTL-2026-000123`.
"# Booking.com" 
