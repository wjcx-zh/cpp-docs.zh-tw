---
title: 屬性對應 |Microsoft Docs
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
ms.openlocfilehash: 8672cca382d89eda93e624f566f754bd2eb14d0a
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083407"
---
# <a name="property-maps"></a>屬性對應

除了工作階段、 資料列集和選擇性的命令物件，每個提供者會支援一或多個屬性。 這些屬性會定義在 OLE DB 提供者精靈所建立的標頭檔中所包含的屬性對應。 每個標頭檔包含的物件或該檔案中定義的物件定義的 OLE DB 屬性群組中的屬性對應。 包含資料來源物件的標頭檔也包含的屬性對應[資料來源屬性](https://msdn.microsoft.com/library/ms724188)。 Session.h 包含的屬性對應[工作階段屬性](/previous-versions/windows/desktop/ms714221)。 在資料列集和命令物件位於單一標頭檔，稱為*projectname*RS.h。 這些屬性屬於[資料列集屬性](/previous-versions/windows/desktop/ms711252)群組。  
  
## <a name="see-also"></a>另請參閱  

[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)