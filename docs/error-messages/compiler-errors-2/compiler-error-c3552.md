---
title: "編譯器錯誤 C3552 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: ae268ae3c0d7857aa2c2cbafe9e158656f657f1a
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3552"></a>編譯器錯誤 C3552
'typename': 晚期指定的傳回類型不能包含 'auto'  
  
 如果您使用 `auto` 關鍵字作為函式之傳回類型的預留位置，則必須提供晚期指定的傳回類型。 不過，您無法使用另一個 `auto` 關鍵字來指定晚期指定的傳回類型。 例如，下列程式碼片段會產生錯誤 C3552。  
  
 `auto myFunction->auto; // C3552`
