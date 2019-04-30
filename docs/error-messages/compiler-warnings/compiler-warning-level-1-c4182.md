---
title: 編譯器警告 (層級 1) C4182
ms.date: 11/04/2016
f1_keywords:
- C4182
helpviewer_keywords:
- C4182
ms.assetid: 8970f3c6-e2dd-407e-b2ec-964360eb8b43
ms.openlocfilehash: 49e3e2f62b4be50d14cb8da3d776b4640be7160c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391630"
---
# <a name="compiler-warning-level-1-c4182"></a>編譯器警告 (層級 1) C4182

\#包含巢狀層級是深度; 'number'可能的無限遞迴

編譯器已用完堆積上的空間，因為巢狀 Include 檔數目太多。 當從另一個 Include 檔包含 Include 檔時即為巢狀 Include 檔。

這個訊息僅供參考，而且前面出現錯誤 [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md)。