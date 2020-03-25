---
title: 嚴重錯誤 C1067
ms.date: 11/04/2016
f1_keywords:
- C1067
helpviewer_keywords:
- C1067
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
ms.openlocfilehash: 3b016790220d409435ff7ea53c6f48899a9e8f1c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204343"
---
# <a name="fatal-error-c1067"></a>嚴重錯誤 C1067

編譯器限制：已超過類型記錄的64K 大小限制

如果符號的裝飾名稱超過247個字元，就會發生此錯誤。  若要解決此問題，請縮短符號名稱。

當編譯器產生了偵錯工具資訊時，它會發出類型記錄來定義在原始程式碼中遇到的類型。  例如，類型記錄包含簡單的結構和函式的引數清單。  其中一些類型記錄可以是大型清單。

任何類型記錄的大小都有64K 的限制。  如果超過64K 限制，則會發生此錯誤。

如果有許多具有完整名稱的符號，或如果類別、結構或等位具有太多成員，也可能會發生 C1067。
