---
title: 屬性對應 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, properties
- maps, property
- property maps
ms.assetid: 44abde56-90ad-4612-854e-d2fa5426fa80
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d7664562ff31f1f5871fab4ce74c1652370a540d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="property-maps"></a>屬性對應
除了工作階段、 資料列集，並選擇性的命令物件，每個提供者會支援一或多個屬性。 這些屬性會定義在 OLE DB 提供者精靈 所建立的標頭檔中所包含的屬性對應。 每個標頭檔包含的物件或該檔案中定義的物件定義的 OLE DB 屬性群組中的屬性對應。 標頭檔，其中包含資料來源物件也包含的屬性對應[DataSource 屬性](https://msdn.microsoft.com/en-us/library/ms724188\(v=vs.140\).aspx)。 Session.h 包含的屬性對應[工作階段屬性](https://msdn.microsoft.com/en-us/library/ms714221.aspx)。 資料列集和命令物件位於單一標頭檔，稱為*projectname*RS.h。 這些屬性屬於[資料列集屬性](https://msdn.microsoft.com/en-us/library/ms711252.aspx)群組。  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)