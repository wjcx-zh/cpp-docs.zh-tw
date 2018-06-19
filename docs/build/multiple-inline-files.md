---
title: 多重內嵌檔 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline files, multiple NMAKE
- multiple inline files
- NMAKE program, inline files
ms.assetid: 6d381dcf-0ed8-45d1-8df3-b4598d860b99
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ee9be15f029c0aaab3ca4bc47fb183e1499c2e2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368209"
---
# <a name="multiple-inline-files"></a>多重內嵌檔
命令可以建立多個內嵌檔案。  
  
## <a name="syntax"></a>語法  
  
```  
  
      command << <<  
inlinetext  
<<[KEEP | NOKEEP]  
inlinetext  
<<[KEEP | NOKEEP]  
```  
  
## <a name="remarks"></a>備註  
 為每個檔案，指定一或多個行內嵌的文字，後面接著包含分隔符號的結尾行。 開始在第一個檔案的分隔列下一行的第二個檔案的文字。  
  
## <a name="see-also"></a>另請參閱  
 [Makefile 中的內嵌檔](../build/inline-files-in-a-makefile.md)