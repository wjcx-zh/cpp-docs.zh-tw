---
title: 編譯器警告 （層級 1） C4276 |Microsoft 文件
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
ms.openlocfilehash: afedab27c2fb93075aa33053c12ec6973824f144
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277302"
---
# <a name="compiler-warning-level-1-c4276"></a>編譯器警告 (層級 1) C4276
'function': 提供; 沒有原型假設沒有參數  
  
 當您採取的函式的位址[__stdcall](../../cpp/stdcall.md)呼叫慣例，您必須提供原型，編譯器可能會建立函式的裝飾的名稱。 因為*函式*沒有原型，編譯器中，建立裝飾的名稱時，假設該函式沒有參數。