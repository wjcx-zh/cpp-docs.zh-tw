---
title: "命令列警告 D9027 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- D9027
dev_langs:
- C++
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 7d569243a6d0d1669a8964ab9c419cb0e7428ba9
ms.lasthandoff: 04/04/2017

---
# <a name="command-line-warning-d9027"></a>命令列警告 D9027
原始程式檔 '\<filename >' 忽略  
  
 CL.exe 忽略的輸入的來源檔案。  
  
 這個警告可能因 /Fo 選項之間的輸出檔名與 /c 選項的命令列上的空間。 例如:   
  
```  
cl /c /Fo output.obj input.c   
```  
  
 因為 /Fo 之間沒有空格和`output.obj`，CL.exe 會採用`output.obj`做為輸入檔的名稱。 若要修正此問題，請將空格移除︰  
  
```  
cl /c /Fooutput.obj input.c   
```
