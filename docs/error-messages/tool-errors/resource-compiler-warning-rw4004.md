---
title: 資源編譯器警告 RW4004
ms.date: 11/04/2016
f1_keywords:
- RW4004
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
ms.openlocfilehash: ca0fb271a5ab43994ec37cc8d59c33877903f6e8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182340"
---
# <a name="resource-compiler-warning-rw4004"></a>資源編譯器警告 RW4004

ASCII 字元不等同虛擬按鍵碼

針對 VIRTKEY 類型快速鍵中的虛擬按鍵碼使用了字串常值。

這則警告允許您繼續進行；但請注意，所產生的快速鍵可能不符合您指定的字串 (VIRTKEY 使用不同於 ASCII 快速鍵的按鍵碼)。

雖然字串常值在語法上是有效的，但您只可以使用**VK_\*** WINDOWS .h 中的 #define 值，確保取得您想要的加速器。
