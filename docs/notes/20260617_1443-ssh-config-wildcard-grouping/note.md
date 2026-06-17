# New Finding: SSH Config Wildcard Grouping Can Significantly Simplify Server Definitions

## Observation

While reviewing another team's SSH configuration, I observed the use of wildcard host grouping to eliminate repeated configuration blocks.

Example:

```sshconfig
Host vultr-*
    User francis
    IdentityFile ~/.ssh/vultr_ed25519
    IdentitiesOnly yes

Host vultr-internal
    HostName 192.0.2.10

Host vultr-airflow3
    HostName 192.0.2.20

Host vultr-app-dev
    HostName 192.0.2.30

Host vultr-app-prod
    HostName 192.0.2.40
```

(Uses documentation-reserved example IP ranges from RFC 5737, not real addresses.)

---

## What We Learned

Rather than repeating the same settings on every host definition, OpenSSH allows host patterns such as:

```sshconfig
Host vultr-*
```

to apply common configuration to every matching host.

This means:

```bash
ssh vultr-internal
```

inherits settings from both:

```sshconfig
Host vultr-*
```

and

```sshconfig
Host vultr-internal
```

reducing duplication and making large SSH configurations easier to maintain.

---

## Supporting Documentation

### OpenBSD OpenSSH Documentation

The OpenSSH documentation states:

> "A pattern consists of zero or more non-whitespace characters, '*', or '?'."

This confirms that wildcard matching is a supported feature of the `Host` directive.

Source:
https://man.openbsd.org/ssh_config

---

### Linux man7 Documentation

The Linux man page states:

> "Host restricts the following declarations ... to be only for those hosts that match one of the patterns given after the keyword."

This confirms that multiple hosts can be grouped under a single pattern definition.

Source:
https://man7.org/linux/man-pages/man5/ssh_config.5.html

---

### Configuration Processing Order

The OpenSSH documentation also states:

> "Since the first obtained value for each parameter is used, more host-specific declarations should be given near the beginning of the file, and general defaults at the end."

Source:
https://man.openbsd.org/ssh_config

This is an important implementation detail because SSH processes matching host entries and merges configuration according to its precedence rules.

---

## Potential Benefit

For environments such as:

- Internal Apps
- Airflow3
- App Dev
- App Prod

where most servers share:

- the same user
- the same SSH key
- the same keepalive settings

a wildcard grouping approach could substantially reduce repetition and simplify long-term maintenance.

Instead of updating four or five separate host definitions when a key changes, a single shared block can be updated.

---

## Recommendation for Evaluation

This appears to be a standard OpenSSH capability rather than a custom convention.

The team may want to evaluate adopting wildcard host grouping for infrastructure organized by provider or environment (for example `vultr-*`, `aws-*`, `prod-*`, or `dev-*`) to reduce duplication and improve maintainability of SSH configuration files.
