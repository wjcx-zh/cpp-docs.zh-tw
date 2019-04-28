---
title: 編譯器警告 (層級 1) C4276
ms.date: 11/04/2016
f1_keywords:
- C4276
helpviewer_keywords:
- C4276
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
ms.openlocfilehash: 87f13f7da12a3f7e40aaad180e2a3bc83e121771
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207135"
---
# <a name="compiler-warning-level-1-c4276"></a>編譯器警告 (層級 1) C4276

'function': 提供; 沒有原型假設沒有參數

當您採取的函式的位址[__stdcall](../../cpp/stdcall.md)呼叫慣例，您必須提供原型，編譯器可能會建立函式的裝飾的名稱。 由於*函式*沒有原型，編譯器中，建立裝飾的名稱時，會假設函式沒有任何參數。