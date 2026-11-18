DRAGONI APP - BASE WEB ONLINE
1. Crea un progetto Supabase e applica schema.sql nel SQL Editor.
2. In Supabase Authentication crea il primo utente, copia il suo UUID, poi esegui:
   insert into public.profiles(id,role) values ('UUID_UTENTE','admin');
3. In Supabase Storage crea un bucket pubblico chiamato news-photos.
   Per consentire gli upload dei soli dirigenti, esegui nel SQL Editor:
   create policy "editor uploads" on storage.objects for insert to authenticated
   with check (bucket_id='news-photos' and public.my_role() in ('admin','redattore'));
   create policy "public photos" on storage.objects for select to anon,authenticated
   using (bucket_id='news-photos');
4. Inserisci Project URL e publishable/anon key in config.js (mai service_role key).
5. Pubblica index.html e config.js su Vercel, con HTTPS.
6. Prova prima l'accesso admin, poi la pubblicazione e la lettura da un altro dispositivo.
7. Il backup JSON del gestionale precedente NON viene importato automaticamente: serve migrazione dedicata.
NOTA: starter da verificare sul progetto reale; non è ancora distribuito, non include modifiche ai contenuti né sincronizzazione Tuttocampo.
