---
title: 編譯器警告 （層級 1） C4182 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4182
dev_langs:
- C++
helpviewer_keywords:
- C4182
ms.assetid: 8970f3c6-e2dd-407e-b2ec-964360eb8b43
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 80c0cdac45238a4734b02d34f4c540c62a2f0c09
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056569"
---
# <a name="compiler-warning-level-1-c4182"></a>編譯器警告 (層級 1) C4182

\#包含巢狀層級是深度; 'number'可能的無限遞迴

編譯器已用完堆積上的空間，因為巢狀 Include 檔數目太多。 當從另一個 Include 檔包含 Include 檔時即為巢狀 Include 檔。

這個訊息僅供參考，而且前面出現錯誤 [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md)。