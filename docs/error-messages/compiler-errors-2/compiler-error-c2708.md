---
title: 編譯器錯誤 C2708 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2708
dev_langs:
- C++
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d30b2e5c1856a604ae314316cd71d6acc00a7c74
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33234756"
---
# <a name="compiler-error-c2708"></a>編譯器錯誤 C2708
'identifier': 實質參數長度 （位元組） 不同於至上一個呼叫或參考  
  
 A [__stdcall](../../cpp/stdcall.md)函式前面必須有原型。 否則，編譯器會解譯為原型函式的第一個呼叫，而且當編譯器遇到不符合的呼叫，就會發生此錯誤。  
  
 若要修正這個錯誤會加入函式原型。