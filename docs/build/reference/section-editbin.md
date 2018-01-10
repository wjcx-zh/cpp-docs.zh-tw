---
title: "-SECTION (EDITBIN) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /section
dev_langs: C++
helpviewer_keywords:
- -SECTION editbin option
- SECTION editbin option
- alignment characters in sections
- /SECTION editbin option
ms.assetid: 4680ab4e-c984-4251-8241-93440cad7615
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 91ffb9bd0645cab51e4140697c41e5b715380fe8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="section-editbin"></a>/SECTION (EDITBIN)
```  
/SECTION:name[=newname][,attributes][alignment]  
```  
  
## <a name="remarks"></a>備註  
 此選項會變更的屬性區段中，覆寫區段的目的檔被編譯或連結時所設定的屬性。  
  
 冒號後面 ( **:** )，指定*名稱*的區段。 若要變更的區段名稱，請遵循*名稱*以等號 （=） 和*newname*區段。  
  
 若要設定或變更區段的`attributes`，指定逗號 (**，**) 後面接著一個或多個屬性的字元。 要變換正負號的屬性，在之前它一個內含驚嘆號 （！） 的字元。 下列字元指定記憶體的屬性：  
  
|屬性|設定|  
|---------------|-------------|  
|c|程式碼|  
|d|可捨棄|  
|e|可執行檔|  
|i|初始化的資料|  
|K|虛擬記憶體快取|  
|m|移除連結|  
|o|連結資訊|  
|p|分頁的虛擬記憶體|  
|r|讀取|  
|秒|共用|  
|u|未初始化的資料|  
|w|寫入|  
  
 控制*對齊*，指定的字元**A**後面接著一個，如下所示設定對齊的大小 （位元組），下列字元：  
  
|字元|對齊大小 （位元組）|  
|---------------|-----------------------------|  
|1|1|  
|2|2|  
|4|4|  
|8|8|  
|p|16|  
|t|32|  
|秒|64|  
|x|沒有對齊|  
  
 指定`attributes`和*對齊*元字元，如同使用任何空格的字串。 這些字元不區分大小寫。  
  
## <a name="see-also"></a>請參閱  
 [EDITBIN 選項](../../build/reference/editbin-options.md)