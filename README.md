<!-- revenuedot:readme:start -->
<p align="center"><a href="https://revenuedot.app"><picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/revenuedot/revenuedot/main/brand/kit/wordmark/revenuedot-lockup-white.svg">
  <img alt="RevenueDot" src="https://raw.githubusercontent.com/revenuedot/revenuedot/main/brand/kit/wordmark/revenuedot-lockup-black.svg" height="40">
</picture></a></p>

# RevenueDot Flutter SDK

This is RevenueDot's MIT fork of RevenueCat's `purchases_flutter`: the same classes and method names, pointed at a RevenueDot server ([RevenueDot Cloud](https://app.revenuedot.app/signup) at `https://api.revenuedot.app`, or one you host) with RevenueDot's response-signing key built in, and kept in sync with upstream.

[![License: MIT](https://img.shields.io/badge/license-MIT-blue)](LICENSE) [![Git tag](https://img.shields.io/github/v/tag/revenuedot/purchases-flutter?filter=*-revenuedot&label=git%20dependency)](https://github.com/revenuedot/purchases-flutter/releases) [![Upstream](https://img.shields.io/badge/upstream-RevenueCat%2Fpurchases--flutter_10.13.2-lightgrey)](https://github.com/RevenueCat/purchases-flutter)

## Install

The package names stay `purchases_flutter` and `purchases_ui_flutter`, so every `import 'package:purchases_flutter/purchases_flutter.dart'` keeps working. The fork ships as a git dependency (the pub.dev names belong to RevenueCat):
```yaml
# pubspec.yaml
dependencies:
  purchases_flutter:
    git:
      url: https://github.com/revenuedot/purchases-flutter.git
      ref: 10.13.2-revenuedot
  purchases_ui_flutter:          # only if you use paywalls
    git:
      url: https://github.com/revenuedot/purchases-flutter.git
      path: purchases_ui_flutter
      ref: 10.13.2-revenuedot
```

## Configure

```dart
import 'dart:io' show Platform;
import 'package:purchases_flutter/purchases_flutter.dart';

Future<void> initPurchases() async {
  // Self-hosted server only: RevenueDot Cloud (https://api.revenuedot.app) is the default.
  await Purchases.setProxyURL('https://revenuedot.example.com');
  await Purchases.configure(PurchasesConfiguration(Platform.isIOS ? 'appl_...' : 'goog_...'));   // each app's public key
}
```

The fork already trusts RevenueDot's signing key, so no signature or verification setting is needed. `Purchases.setProxyURL` works on Flutter web with this fork. Full guide: https://revenuedot.app/docs/sdks/flutter.

## What RevenueDot adds

- **Start free on [RevenueDot Cloud](https://app.revenuedot.app/signup)**: free up to $10,000 a month of tracked revenue, then 0.5%, never more than $999 a month ([pricing](https://revenuedot.app/pricing)).
- **The same REST API and webhook payloads** as RevenueCat, so your backend and integrations keep working ([API reference](https://revenuedot.app/docs/api)).
- **Paywalls, experiments and the Customer Center** built in the RevenueDot dashboard and rendered by this SDK ([guides](https://revenuedot.app/docs/guides)).
- **A one-line migration:** point the stock SDK at RevenueDot with `setProxyURL`, or install this fork and drop the line ([migration guide](https://revenuedot.app/docs/migrate)).

## Use with your coding agent

Coding agents can read this repository's docs and code on demand, so they use the right package and imports:

- **Context7:** https://context7.com/revenuedot/purchases-flutter
- **DeepWiki:** https://deepwiki.com/revenuedot/purchases-flutter
- **GitMCP:** https://gitmcp.io/revenuedot/purchases-flutter

## Links

- **Docs for this SDK:** https://revenuedot.app/docs/sdks/flutter
- **Example app:** https://github.com/revenuedot/examples/tree/main/mobile/flutter
- **Releases and changelog:** https://github.com/revenuedot/purchases-flutter/releases (tags `<upstream version>-revenuedot`; upstream's changes are in `CHANGELOG.md`)
- **RevenueDot server and dashboard:** https://github.com/revenuedot/revenuedot
- **Fork pipeline (what we change and how upstream is merged):** https://github.com/revenuedot/revenuedot/tree/main/scripts/forks

RevenueDot is not affiliated with RevenueCat, Inc. RevenueCat's copyright notice stays in `LICENSE`; RevenueDot's changes are MIT too.

---

## Upstream README (RevenueCat's, unchanged)
<!-- revenuedot:readme:end -->

<p align="center">
  <img src="https://uploads-ssl.webflow.com/5e2613cf294dc30503dcefb7/5e752025f8c3a31d56a51408_logo_red%20(1).svg" width="350" alt="RevenueCat"/>
<br>
  
[![pub package](https://img.shields.io/pub/v/purchases_flutter.svg)](https://pub.dartlang.org/packages/purchases_flutter)

## purchases_flutter

*purchases_flutter* is a client for the [RevenueCat](https://www.revenuecat.com/) subscription and purchase tracking system. It is an open source framework that provides a wrapper around `StoreKit`, `Google Play Billing` and the RevenueCat backend to make implementing in-app subscriptions in `Flutter` easy - receipt validation and status tracking included!

## Features
|   | RevenueCat |
| --- | --- |
✅ | Server-side receipt validation
➡️ | [Webhooks](https://docs.revenuecat.com/docs/webhooks) - enhanced server-to-server communication with events for purchases, renewals, cancellations, and more  
🎯 | Subscription status tracking - know whether a user is subscribed whether they're on iOS or Android
📊 | Analytics - automatic calculation of metrics like conversion, mrr, and churn  
📝 | [Online documentation](https://docs.revenuecat.com/docs/flutter) and [SDK Reference](https://pub.dev/documentation/purchases_flutter/latest/) up to date  
🔀 | [Integrations](https://www.revenuecat.com/integrations) - over a dozen integrations to easily send purchase data where you need it  
💯 | Well maintained - [frequent releases](https://github.com/RevenueCat/purchases-flutter/releases)  
📮 | Great support - [Help Center](https://revenuecat.zendesk.com) 

## Installation
To use this plugin, add `purchases_flutter` as a [dependency in your pubspec.yaml file](https://flutter.io/platform-plugins/).

### Requirements
*purchases_flutter* requires Xcode 14.0+ and minimum targets iOS 13.0+/Android SDK 21+ (Android 5.0+).

## SDK Reference
 Our full SDK reference [can be found here](https://pub.dev/documentation/purchases_flutter/latest/).

## Getting Started
For more detailed information, you can view our complete documentation at [docs.revenuecat.com](https://docs.revenuecat.com/docs/flutter).
