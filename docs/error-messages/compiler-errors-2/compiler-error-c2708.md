---
title: "編譯器錯誤 C2708 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2708
dev_langs:
- C++
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 495fd9aeaad785edd8653e46ae666f60c337b12d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2708"></a>編譯器錯誤 C2708
'identifier': 實質參數長度 （位元組） 不同於至上一個呼叫或參考  
  
 A [__stdcall](../../cpp/stdcall.md)函式前面必須有原型。 否則，編譯器會解譯為原型函式的第一個呼叫，而且當編譯器遇到不符合的呼叫，就會發生此錯誤。  
  
 若要修正這個錯誤會加入函式原型。