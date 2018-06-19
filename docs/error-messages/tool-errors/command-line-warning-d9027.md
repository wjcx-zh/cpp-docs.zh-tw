---
title: 命令列警告 D9027 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9027
dev_langs:
- C++
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfe2493290c4e4cc5b744136b8e7036c6559220a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301446"
---
# <a name="command-line-warning-d9027"></a>命令列警告 D9027
原始程式檔 '\<檔案名稱 >' 忽略  
  
 CL.exe 忽略的輸入的來源檔案。  
  
 這個警告可能因 /Fo 選項之間的輸出檔名與 /c 選項的命令列上的空間。 例如:   
  
```  
cl /c /Fo output.obj input.c   
```  
  
 因為 /Fo 之間沒有空格和`output.obj`，CL.exe 會採用`output.obj`做為輸入檔的名稱。 若要修正此問題，請將空格移除：  
  
```  
cl /c /Fooutput.obj input.c   
```