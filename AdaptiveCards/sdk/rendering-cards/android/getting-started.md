---
title: Android SDK
author: bekao
ms.author: bekao
ms.date: 09/27/2017
ms.topic: article
ms.openlocfilehash: 4723175bf94685c22d99fb15f3d1887ac37b8c57
ms.sourcegitcommit: 6889c7e1a38029d965c8f91dc9108819dbdea552
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68733008"
---
# <a name="getting-started---android"></a>Guida introduttiva-Android

Si tratta di un renderer che è destinato ai controlli nativi Android.

## <a name="install-maven-package"></a>Installare il pacchetto Maven

[![Maven centrale](https://img.shields.io/maven-central/v/io.adaptivecards/adaptivecards-android.svg)](https://search.maven.org/#search%7Cga%7C1%7Ca%3A%22adaptivecards-android%22)

È possibile trovare i pacchetti pubblicati ![qui](https://search.maven.org/search?q=g:io.adaptivecards)

Per includere la libreria nel progetto, è necessario includere questa riga nel progetto Gradle. Build nella sezione dipendenze

```build.gradle
 implementation 'io.adaptivecards:adaptivecards-android:1.1.0'
```
È necessario modificare il numero di versione in base alla versione che si vuole includere nel progetto

## <a name="add-import"></a>Aggiungi importazione

Per includere il modello a oggetti, aggiungere questa importazione

```
 import io.adaptivecards.objectmodel.*;
```

Per includere il renderer, aggiungere questa importazione

```
 import io.adaptivecards.renderer.*;
```

## <a name="next-steps"></a>Passaggi successivi

Vedere [eseguire il rendering di una scheda](render-a-card.md) per i passaggi successivi.
