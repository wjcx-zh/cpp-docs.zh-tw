---
title: "區段 （C/C + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SECTIONS
dev_langs: C++
helpviewer_keywords: SECTIONS .def file statement
ms.assetid: 7b974366-9ef5-4e57-bbcc-73a1df6f8857
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9d1564d068f4d69c3190b8bb24a32e7efb01dbef
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="sections-cc"></a>SECTIONS (C/C++)
導入了一個或多個區段`definitions`所存取規範，在您的專案輸出檔案中的區段。  
  
```  
SECTIONS  
definitions  
```  
  
## <a name="remarks"></a>備註  
 每一個定義都必須在不同的行上。 `SECTIONS`或前一行的第一個定義的同一行上，可以是關鍵字。 .Def 檔可以包含一或多個`SECTIONS`陳述式。  
  
 這`SECTIONS`陳述式在映像檔中，設定一或多個區段的屬性，並可用來覆寫區段的每個類型的預設屬性。  
  
 格式`definitions`是：  
  
 `.section_name specifier`  
  
 其中`.section_name`程式映像中的區段名稱和`specifier`是一或多個下列存取修飾詞：  
  
|修飾詞|說明|  
|--------------|-----------------|  
|`EXECUTE`|區段，則可執行檔|  
|`READ`|允許對於資料的讀取的作業|  
|`SHARED`|共用區段載入影像的所有處理程序|  
|`WRITE`|允許對於資料的寫入作業|  
  
 以空格分隔規範的名稱。 例如：  
  
```  
SECTIONS  
.rdata READ WRITE  
```  
  
 `SECTIONS`標記區段的清單開頭`definitions`。 每個`definition`必須另起一行。 `SECTIONS`關鍵字可以在同一行與第一個`definition`或前一行上。 .Def 檔可以包含一或多個`SECTIONS`陳述式。 `SEGMENTS`同義支援關鍵字`SECTIONS`。  
  
 舊版的 Visual c + + 支援：  
  
```  
section [CLASS 'classname'] specifier  
```  
  
 `CLASS`關鍵字是支援的相容性，但會被忽略。  
  
 若要指定區段屬性對等的方法是使用[/section](../../build/reference/section-specify-section-attributes.md)選項。  
  
## <a name="see-also"></a>另請參閱  
 [模組定義陳述式的規則](../../build/reference/rules-for-module-definition-statements.md)