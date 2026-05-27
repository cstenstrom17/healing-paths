# Healing Paths

A clean, professional resource for finding programs and sharing recovery experiences.

## Setup

### Prerequisites
- Node.js 16+
- npm or yarn

### Installation

1. **Clone and install dependencies:**
   ```bash
   npm install
   ```

2. **Environment variables are already set in `.env.local`**
   - `NEXT_PUBLIC_SUPABASE_URL` - Your Supabase project URL
   - `NEXT_PUBLIC_SUPABASE_ANON_KEY` - Your Supabase anonymous key

3. **Run the development server:**
   ```bash
   npm run dev
   ```
   
   Open [http://localhost:3000](http://localhost:3000) in your browser.

## Project Structure

```
pages/
  ├── index.js                    # Landing page
  ├── browse.js                   # Browse all schools
  └── schools/[id].js             # Dynamic school detail page

components/
  └── layout.js                   # Shared layout with navigation

lib/
  └── supabase.js                 # Supabase client

styles/
  ├── globals.css                 # Global styles & variables
  ├── layout.module.css           # Header/footer styles
  ├── home.module.css             # Landing page styles
  ├── browse.module.css           # Browse page styles
  └── school-detail.module.css    # Detail page styles
```

## Features

- **Landing/About page** - Sets context and explains the resource
- **Browse page** - Lists all approved schools with location info
- **Dynamic detail pages** - Pulled directly from Supabase
- **Review system** - Anonymous or named reviews (unapproved until you review them)
- **Professional design** - Refined, respectful aesthetic

## Supabase Tables

### `schools`
- `id` - Unique identifier
- `name` - School/program name
- `address`, `city`, `state`, `zip` - Location info
- `owner` - Contact or owner info
- `is_approved` - Visibility (only approved schools show)
- `is_open` - Status badge
- `created_on` - Timestamp

### `reviews`
- `id` - Unique identifier
- `school_id` - Foreign key to schools table
- `author` - Reviewer name (can be blank for anonymous)
- `rating` - 1-5 rating
- `text` - Review content
- `is_approved` - Visibility (only approved reviews show)
- `created_at` - Timestamp

## Adding a School

In Supabase, insert a new row in the `schools` table:
- Set `is_approved = true` to make it visible
- Set `is_open = true/false` for the status badge
- Fill in name and location fields

## Next Steps

1. **Admin dashboard** - Panel to approve/reject schools and reviews
2. **Search & filtering** - Filter by state, open/closed status
3. **More metadata** - Cost, specialties, contact info, etc.
4. **User accounts** (optional) - Track submissions, edit reviews

## Deployment

### Vercel (Recommended for Next.js)
1. Push to GitHub
2. Connect repo to Vercel
3. Set environment variables
4. Deploy

### Other platforms
- Netlify
- Railway
- Render
- Digital Ocean

## Styling Notes

The site uses a refined, professional aesthetic:
- **Typography:** Noto Serif for headings, Inter for body
- **Colors:** Blue accent (#2c5aa0), neutral grays, reserved use of status colors
- **Spacing:** Generous margins and padding
- **Interactions:** Subtle transitions and hover states

All styling is in CSS modules for component scope and maintainability.
