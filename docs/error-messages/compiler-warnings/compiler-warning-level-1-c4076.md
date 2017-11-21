---
title: "編譯器警告 （層級 1） C4076 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4076
dev_langs: C++
helpviewer_keywords: C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9b361448f7181ed4fd044ec18a7b36c4f86012fb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4076"></a>編譯器警告 (層級 1) C4076
'typemod': 無法與類型 'typename' 搭配使用  
  
 類型修飾詞 (不論是 **signed** 還是 `unsigned`) 不能與非整數類型搭配使用。 會忽略***typemod*** 。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4076：  
  
```  
// C4076.cpp  
// compile with: /W1 /LD  
unsigned double x;   // C4076  
```