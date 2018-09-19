---
title: 資源編譯器警告 RW4004 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW4004
dev_langs:
- C++
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33305f1f86c0cc1722e4a235ec27927f6e70675f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46095985"
---
# <a name="resource-compiler-warning-rw4004"></a>資源編譯器警告 RW4004

ASCII 字元不等同虛擬按鍵碼

針對 VIRTKEY 類型快速鍵中的虛擬按鍵碼使用了字串常值。

這則警告允許您繼續進行；但請注意，所產生的快速鍵可能不符合您指定的字串 (VIRTKEY 使用不同於 ASCII 快速鍵的按鍵碼)。

雖然字串常值語法有效，才能確保您取得您想要使用的加速器**VK_\* #define**在 WINDOWS.h 中的值。