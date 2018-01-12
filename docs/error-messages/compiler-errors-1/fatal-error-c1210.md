---
title: "嚴重錯誤 C1210 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C1210
dev_langs: C++
helpviewer_keywords: C1210
ms.assetid: e2208309-c284-425c-a7e8-48e96e66f35b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c11ed9df47ae7fc607189683b52a35779e485996
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1210"></a>嚴重錯誤 C1210
所安裝的執行階段版本不支援 /clr:pure 和 /clr:safe  
  
 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代。  
  
 如果您有目前版本的編譯器，但 Common Language Runtime 來自舊版本，就會發生 C1210。  
  
 編譯器的某個功能可能無法在執行階段的舊版本上運作。  
  
 若要解決 C1210，請安裝要與編譯器搭配使用的 Common Language Runtime 版本。