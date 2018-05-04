---
title: 名稱 （C/C + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- name
dev_langs:
- C++
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a94b82a65cf68d9802d7bf9620e4128ab6b35071
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="name-cc"></a>NAME (C/C++)
指定主要輸出檔的名稱。  
  
```  
NAME [application][BASE=address]  
```  
  
## <a name="remarks"></a>備註  
 指定輸出檔案名稱相同的方法是使用[/out](../../build/reference/out-output-file-name.md)連結器選項和設定基底地址的對等方式，都[/基底](../../build/reference/base-base-address.md)連結器選項。 如果同時指定這兩者，/OUT 覆寫**名稱**。  
  
 如果您建立 DLL 時，名稱只會影響 DLL 名稱。  
  
## <a name="see-also"></a>另請參閱  
 [模組定義陳述式的規則](../../build/reference/rules-for-module-definition-statements.md)