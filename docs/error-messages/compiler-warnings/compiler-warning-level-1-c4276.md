---
title: 編譯器警告 （層級 1） C4276 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4276
dev_langs:
- C++
helpviewer_keywords:
- C4276
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 40a6c85b460e9718a8816598afb016e9c7a493b9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116018"
---
# <a name="compiler-warning-level-1-c4276"></a>編譯器警告 (層級 1) C4276

'function': 提供; 沒有原型假設沒有參數

當您採取的函式的位址[__stdcall](../../cpp/stdcall.md)呼叫慣例，您必須提供原型，編譯器可能會建立函式的裝飾的名稱。 由於*函式*沒有原型，編譯器中，建立裝飾的名稱時，會假設函式沒有任何參數。