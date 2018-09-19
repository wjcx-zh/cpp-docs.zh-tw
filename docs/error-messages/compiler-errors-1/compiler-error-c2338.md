---
title: 編譯器錯誤 C2338 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2338
dev_langs:
- C++
helpviewer_keywords:
- C2338
ms.assetid: 49bba575-1de4-4963-86c6-ce3226a2ba51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 77bc98afdad36e0505abb58ee06ec1c7e7654ae5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071571"
---
# <a name="compiler-error-c2338"></a>編譯器錯誤 C2338

> *錯誤訊息*

此錯誤可能因`static_assert`編譯期間發生錯誤。 訊息由提供`static_assert`參數。

也可以由外部提供者，編譯器產生這個錯誤訊息。 在大部分情況下，屬性提供者 DLL，例如 ATLPROV 報告這些錯誤。 此訊息的一些常見的形式包括：

> '*屬性*' Atl 屬性提供者： 錯誤 ATL*數目**訊息*

> 不正確的使用方式的屬性 '*屬性*'

> '*使用量*': 屬性 [使用量] 的格式不正確

這些錯誤通常是無法復原，並且之後可能會嚴重編譯器錯誤。

若要修正這些問題，更正屬性使用方式。 例如，在某些情況下，屬性參數必須宣告才能使用。 如果提供的 ATL 錯誤號碼，請檢查該錯誤，如需特定資訊的文件。
