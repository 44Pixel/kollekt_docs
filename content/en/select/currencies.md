---
title: Currencies
description: ""
position: 1001
category: "SELECT"
currencyPlaces:
  ["Workspace currency", "Selection currency", "User currency", "Team currency"]
currencyPriority:
  [
    "Selection currency",
    "User currency",
    "Workspace currency",
    "First available currency on the product",
  ]
---

The currencies a user is shown for any given product when making selection input (either on the dashboard or the iOS app) follows a hierarchy of rules.

## Setting currencies

There are 4 levels where a currency can be set:
<list :items="currencyPlaces">

### Workspace currency

Can currently only be set by Kollekt system admins.

### Selection currency

Defined for an individual selection

### Team currency

Defined for an individual team.
Has no effect on the shown currency.

When a team is added to a selection with no currency set, the selection will get the currency of the added team.

### User currency

Definied for an individual workspace user.

A user can have a different default currency on their different workspaces.

## Determining the shown currency

The shown currency is the first available currency on the product, following the priority below:
<list :items="currencyPriority">
