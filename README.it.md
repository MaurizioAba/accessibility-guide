# 📘 Accessibility Best Practices in Web Development (WCAG)

> Available in:
> - 🇮🇹 [Italiano](./README.it.md)

Guida pratica per costruire **interfacce React accessibili**, basata su [WCAG](https://www.w3.org/WAI/standards-guidelines/wcag/) e le best practice condivise dalla community.

> Questa guida è pensata per sviluppatori scritta in italiano che vogliono scrivere codice **inclusivo**, **navigabile da tastiera**, compatibile con screen reader e più sostenibile per tuttə.

---

## 🚀 Obiettivi

- Usare correttamente la semantica HTML.
- Implementare navigazione con tastiera.
- Scrivere componenti React con accessibilità in mente.
- Evitare pattern problematici per chi ha disabilità visive, motorie o cognitive.

---

## Strumenti consigliati

- axe DevTools – Analisi accessibilità nel browser
- Lighthouse – Audit performance & a11y
- eslint-plugin-jsx-a11y – Linter accessibilità JSX
- React ARIA – Componente ARIA-ready

## Risorse utili

- WCAG 2.2 Quick Reference
- MDN Accessibility Guide
- A11Y Project
- Inclusive Components

## Best Practice

### 1. **Semantica HTML**
- Usa tag corretti: `button`, `header`, `nav`, `main`, `footer`, `form`, ecc.
- Non sostituire i tag semantici con `div` e `span`.

### 2. **Navigazione da tastiera**
- Ogni interazione dev'essere possibile con `Tab`, `Enter` e `Space`.
- Evita `div onClick` non focusabili.

### 3. **Uso degli attributi ARIA**
- Usa `aria-label`, `aria-describedby`, `role="alert"` dove necessario.
- Non abusare: prima preferisci semantica nativa.

### 4. **Gestione del focus**
- Usa `tabIndex={0}` per elementi custom focusabili.
- Usa `ref` e `element.focus()` per gestire flussi dinamici (es. modali, skip links).

### 5. **Form accessibili**
- Associa `label` ai campi (`htmlFor`, `id`).
- Mostra errori con `role="alert"`.
- Includi istruzioni con `aria-describedby`.

### 6. **Colori e contrasti**
- Verifica contrasto minimo 4.5:1 per testo normale.
- Usa [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/).

### 7. **Skip to content**
Permetti agli utenti di saltare direttamente al contenuto.
`<a href="#main-content" className="sr-only focus:not-sr-only">Salta al contenuto</a>`

### 8. **Preferisci elementi interattivi nativi**
Evita di reinventare elementi come pulsanti o link usando <div> o <span> con onClick. Questo tipo di approccio rompe l’accessibilità perché:

Non sono focusabili da tastiera senza tabIndex.

Non attivano comportamenti attesi (es. Enter o Space).

Non hanno ruoli (role) e annunci screen reader predefiniti.

Usare e preferire SEMPRE elementi nativi come:
`<button> per azioni (submit, toggle, modale…)
<a href> per la navigazione
<input> e <textarea>` per i moduli

### 9. **Usa alt test descrittivi per le immagini**
Le immagini devono sempre avere l’attributo alt, per garantire la fruibilità da parte di chi utilizza tecnologie assistive.
Decorative: usa alt="" per evitare lettura inutile da parte dei lettori di schermo.

`<img src="profilo.png" alt="Foto profilo di Mario Rossi" />`

### 10. **Titoli strutturati (h1-h6)**
Usa titoli in ordine gerarchico.

Non saltare livelli (es. non usare h3 senza h2).

### 11. **Responsività accessibile**
Controlla che i contenuti siano leggibili anche su zoom 200%.
Evita contenuti bloccati in orizzontale.

### 12. **Stati visivi e focus**
Assicurati che il focus sia visibile (es. bordo, ombra).

Usa :focus-visible o outline per coerenza.

### 13. **Gestione delle notifiche**
Usa role="status" o role="alert" per annunciare messaggi dinamici.

Esempio: “Elemento aggiunto al carrello”.

### 14. **Lettori di schermo**
Testa con VoiceOver, NVDA o JAWS.

Verifica la lettura coerente di contenuti e moduli.

### 15. **Animazioni e motion**
Evita animazioni complesse o rapide.

Rispetta prefers-reduced-motion per chi le disattiva.

### 16. **ARIA Live Regions**
Usa aria-live="polite" o aria-live="assertive" per aggiornamenti dinamici.

Esempio: risultati filtrati in tempo reale.

### 17. **Landmark roles**
Usa landmark semantici `"(<main>, <nav>, <aside>)" oppure role="main" `ecc.

Aiutano la navigazione via screen reader.

### 18. **Contenuti multimediali**
Video: sempre sottotitoli.

Audio: trascrizioni testuali disponibili.

### 19. **Gestione degli errori nei form**
Evidenzia errori con colori e testo (non solo rosso).

Usa aria-invalid="true" e aria-describedby.

### 20. **Accessibilità nei componenti custom**
Quando crei modali, dropdown o menu:
Chiudi con Esc
Focus loop
Annunci tramite aria-labelledby
