# RacketService

Verwaltungs-App für Bespannungsservice Lisa-Marie Wurst.

## Funktionen

- Registrierung und Anmeldung per Supabase
- Kunden sehen nur ihre eigenen Aufträge und Schläger
- Admins verwalten alle Kunden, Schläger und Aufträge
- Registrierung legt automatisch einen Profil-Eintrag in `public.customers` an

## Supabase-Ergänzung

Die Tabelle `public.customers` benötigt zusätzlich eine optionalen Admin-Schalter:

```sql
alter table public.customers add column if not exists is_admin boolean default false;

create policy "admins_read_customers"
on public.customers for select
using (
  (select is_admin from public.customers where id = auth.uid())
  or id = auth.uid()
);
```

Erstelle für Schläger und Aufträge Tabellen mit einer `customer_id`-Spalte und aktiviertem RLS. Ordne den Admin über `is_admin = true` zu.
