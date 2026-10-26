# Midwifery project questionnaire

Static site with a two-part client questionnaire. No build step.

| Path | What it is |
| --- | --- |
| `/part-1/` | Part 1 – the essentials (send first, about 10 minutes) |
| `/part-2/` | Part 2 – the details (send after the first call) |
| `/` | Forwards to Part 1 |

## Where answers go

Each submission is:

1. **Saved in Supabase**: project `midwifery-questionnaire` (London, eu-west-2), table `public.questionnaire_responses`. Row-level security allows visitors to *insert only*; they can never read, edit or delete answers. View responses in the Supabase dashboard → Table Editor.
2. **Emailed** to `webmaster@estherbodylawson.com` via FormSubmit. The first submission triggers a one-time activation email; click the link once.

If either one fails, the other still captures the answers.

Settings live in the `CONFIG` block near the top of the `<script>` in each `index.html`.

## Deploy on Vercel

1. In Vercel, choose **Add New → Project** and import this GitHub repository.
2. Framework preset: **Other**. Leave build and output settings empty.
3. Deploy. Vercel gives a temporary `*.vercel.app` address; you can rename it under Settings → Domains.

Every push to the main branch redeploys automatically.

## Data notes

The questionnaire collects business information only, not patient data. The Supabase publishable key in the HTML is designed to be public. Access is controlled by the table's row-level security policy.
