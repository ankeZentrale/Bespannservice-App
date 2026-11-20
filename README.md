# RacketService

Verwaltungs-App für den Bespannungsservice Lisa-Marie Wurst.

## Kunde

- Registrierung und Anmeldung
- Kontaktdaten und Adresse verwalten
- Über **Neuer Auftrag** einen Schläger mit Saite, Zuggewicht und Bemerkung erfassen
- Aufträge können nur für den eigenen Account angelegt und eingesehen werden

## Admin

- Alle Kunden anzeigen
- Alle Schläger anzeigen
- Alle Aufträge anzeigen
- Kundenrollen über das Feld `is_admin` in `public.customers` verwalten

## Supabase

Für Aufträge werden die Tabellen `rackets` und `orders` mit den Spalten `customer_id`, `model`, `grip`, `racket_id`, `string`, `tension`, `status`, `notes` und `created_at` benötigt.

Die Kundenrichtlinien erlauben das Einfügen und Lesen eigener Daten. Adminzugriffe werden über `public.is_racketservice_admin()` gesteuert.
