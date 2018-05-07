---
title: 嚴重錯誤 C1210 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1210
dev_langs:
- C++
helpviewer_keywords:
- C1210
ms.assetid: e2208309-c284-425c-a7e8-48e96e66f35b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: df1b970454af8ab692aea949d437e4c1cce4e0cb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1210"></a>嚴重錯誤 C1210
所安裝的執行階段版本不支援 /clr:pure 和 /clr:safe  
  
 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代。  
  
 如果您有目前版本的編譯器，但 Common Language Runtime 來自舊版本，就會發生 C1210。  
  
 編譯器的某個功能可能無法在執行階段的舊版本上運作。  
  
 若要解決 C1210，請安裝要與編譯器搭配使用的 Common Language Runtime 版本。