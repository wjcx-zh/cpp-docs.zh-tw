---
title: "編譯器錯誤 C3552 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3552
dev_langs:
- C++
helpviewer_keywords:
- C3552
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
caps.latest.revision: 4
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 54526c39a928cc534ba815ef8fda802db85f4020
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3552"></a>編譯器錯誤 C3552
'typename': 晚期指定的傳回類型不能包含 'auto'  
  
 如果您使用 `auto` 關鍵字作為函式之傳回類型的預留位置，則必須提供晚期指定的傳回類型。 不過，您無法使用另一個 `auto` 關鍵字來指定晚期指定的傳回類型。 例如，下列程式碼片段會產生錯誤 C3552。  
  
 `auto myFunction->auto; // C3552`
