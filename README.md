# savant-snippets

Savant home automation programming snippets, common integration patterns, and gotchas. Built from real installs.

All site-specific info (IP addresses, device names, credentials) has been removed and replaced with placeholders.

---

## Structure

```
savant-snippets/
├── services/       — Common service definitions
├── states/         — State variable patterns
├── events/         — Event and trigger examples
├── integrations/   — Third-party device integrations
└── troubleshooting/ — Common issues and fixes
```

---

## Requirements

- Savant Pro Host or RacePoint Blueprint
- Blueprint 8.x+
- Basic understanding of Savant service/state model

---

## Notes

These are reference snippets — not plug-and-play imports. Adapt component addresses, zone names, and credentials to your install. Always test in a staging environment before pushing to a live system.

---

## Contributing

If you have sanitized snippets worth sharing, PRs are welcome. Make sure all IP addresses, MAC addresses, usernames, passwords, and site-specific identifiers are replaced with placeholders before submitting.
