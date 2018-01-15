---
title: "虛設常式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: STUB
dev_langs: C++
helpviewer_keywords: STUB .def file statement
ms.assetid: 0a3b9643-19ed-47e9-8173-ee16bc8ed056
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 58430f8211f8859b65103b53d1f98a173c4635ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="stub"></a>STUB
建立虛擬裝置驅動程式 (VxD) 模組定義檔中使用時，可讓您指定檔案名稱包含 （定義於 WINNT IMAGE_DOS_HEADER 結構。H) 以用於虛擬裝置驅動程式 (VxD)，而不是預設的標題。  
  
```  
STUB:filename  
```  
  
## <a name="remarks"></a>備註  
 若要指定另一種方式*filename*與[/虛設常式](../../build/reference/stub-ms-dos-stub-file-name.md)連結器選項。  
  
 虛設常式時為有效的模組定義檔中只建置 VxD。  
  
## <a name="see-also"></a>請參閱  
 [模組定義陳述式的規則](../../build/reference/rules-for-module-definition-statements.md)