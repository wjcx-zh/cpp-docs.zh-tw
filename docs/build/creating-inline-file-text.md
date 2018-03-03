---
title: "建立內嵌檔文字 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- inline files, creating text
- NMAKE program, inline files
- text, inline file
ms.assetid: b8a332ed-8244-4ff8-89e6-029d7f659725
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dcc27a303e9d03d2e899a76703bcfae5abfd0c04
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="creating-inline-file-text"></a>建立內嵌檔文字
內嵌檔是暫時性或永久性。  
  
## <a name="syntax"></a>語法  
  
```  
  
      inlinetext  
.  
.  
.  
<<[KEEP | NOKEEP]  
```  
  
## <a name="remarks"></a>備註  
 指定*inlinetext*命令之後的第一行上。 在不同行的開頭使用雙角括弧 (<<) 標記結尾。 檔案包含所有*inlinetext*分隔的方括號之前。 *Inlinetext*可以有巨集展開和替代項目，但不是指示詞或 makefile 註解。 空格、 定位點和新行字元會被視為常值。  
  
 暫存檔案存在工作階段期間，其他命令可以重複使用。 指定**保留**檔案保留在 NMAKE 工作階段; 之後的右角括號之後未命名的檔案會保留為產生的檔案名稱的磁碟上。 指定**NOKEEP**或 nothing 為暫存檔。 **保留**和**NOKEEP**不區分大小寫。  
  
## <a name="see-also"></a>請參閱  
 [Makefile 中的內嵌檔](../build/inline-files-in-a-makefile.md)