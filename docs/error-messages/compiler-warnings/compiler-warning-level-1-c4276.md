---
title: "編譯器警告 （層級 1） C4276 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4276
dev_langs: C++
helpviewer_keywords: C4276
ms.assetid: 9d738c2d-29e5-408a-b9ff-be1a850b2238
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 609acf714cc149d7a12d515b991fa78c40244129
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4276"></a>編譯器警告 (層級 1) C4276
'function': 提供; 沒有原型假設沒有參數  
  
 當您採取的函式的位址[__stdcall](../../cpp/stdcall.md)呼叫慣例，您必須提供原型，編譯器可能會建立函式的裝飾的名稱。 因為*函式*沒有原型，編譯器中，建立裝飾的名稱時，假設該函式沒有參數。