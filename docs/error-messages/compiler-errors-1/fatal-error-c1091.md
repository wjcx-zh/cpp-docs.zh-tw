---
title: "嚴重錯誤 C1091 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1091
dev_langs:
- C++
helpviewer_keywords:
- C1091
ms.assetid: 812d4201-9154-48b0-b9af-5959c082ca33
caps.latest.revision: 8
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: f014e2b9d34cdac17adefe88c4947ee5fb66cfcc
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="fatal-error-c1091"></a>嚴重錯誤 C1091
編譯器限制：字串長度超過 'length' 個位元組的上限  
  
 字串常數超過目前的字串長度限制。  
  
 您可能想要將靜態字串分割成兩個 （或以上） 的變數，並使用[strcpy_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)將結果聯結做為宣告的或在執行階段的一部分。
