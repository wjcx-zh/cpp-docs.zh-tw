---
title: 嚴重錯誤 1311
ms.date: 11/04/2016
f1_keywords:
- C1311
helpviewer_keywords:
- C1311
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
ms.openlocfilehash: e57e4e0899a5f9d81e87a203b1b699cef0884f0d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203264"
---
# <a name="fatal-error-c1311"></a>嚴重錯誤 1311

COFF 格式無法以靜態方式初始化具有位址數位位元組的 ' var '

在編譯時期，其值不是已知的位址無法以靜態方式指派給其類型具有小於四個位元組之儲存區的變數。

這種錯誤可能會發生在程式碼上C++，否則就是有效的。

下列範例示範了一種可能會造成 C1311 的情況。

```
char c = (char)"Hello, world";   // C1311
char *d = (char*)"Hello, world";   // OK
```
