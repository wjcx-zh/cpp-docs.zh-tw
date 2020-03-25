---
title: 編譯器警告（層級1） C4049
ms.date: 11/04/2016
f1_keywords:
- C4049
helpviewer_keywords:
- C4049
ms.assetid: d11c1870-bcfc-4d71-8945-b87ec6ec3514
ms.openlocfilehash: 214ccae5d9835bc4a3b66bbbe1cd5ded4bc651cb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164140"
---
# <a name="compiler-warning-level-1-c4049"></a>編譯器警告（層級1） C4049

編譯器限制：已發出的終止行號

檔案包含超過16777215（2個<sup>24</sup>-1）行的原始碼。 編譯器會在16777215停止編號。

針對第16777215行之後的程式碼：

- 影像不會包含行號的任何偵錯工具資訊。

- 某些診斷可能會以不正確的行號回報。

- .asm 清單（/FAs）可能有不正確的行號。
