---
title: 資源編譯器警告 RW4004
ms.date: 11/04/2016
f1_keywords:
- RW4004
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
ms.openlocfilehash: bafd1084a665fc656fe184064a48e5fffc61c957
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346076"
---
# <a name="resource-compiler-warning-rw4004"></a>資源編譯器警告 RW4004

ASCII 字元不等同虛擬按鍵碼

針對 VIRTKEY 類型快速鍵中的虛擬按鍵碼使用了字串常值。

這則警告允許您繼續進行；但請注意，所產生的快速鍵可能不符合您指定的字串 (VIRTKEY 使用不同於 ASCII 快速鍵的按鍵碼)。

雖然字串常值語法有效，才能確保您取得您想要使用的加速器**VK_\* #define**在 WINDOWS.h 中的值。