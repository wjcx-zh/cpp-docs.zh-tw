---
title: 屬性對應
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB providers, properties
- maps, property
- property maps
ms.assetid: 44abde56-90ad-4612-854e-d2fa5426fa80
ms.openlocfilehash: 79a65290c24ab016d9f81b54b9b7720d5c4ff352
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "70311686"
---
# <a name="property-maps"></a>屬性對應

使用會話、資料列集和選擇性命令物件，每個提供者都支援一個或多個屬性。 這些屬性是在儲存于**OLE DB 提供者 Wizard**所建立之標頭檔中的屬性對應中定義。 每個標頭檔都會在針對該檔案中定義的物件或物件定義的 OLE DB 屬性群組中，包含屬性的對應。 包含資料來源物件的標頭檔也包含[DataSource 屬性](/previous-versions/windows/desktop/ms724188(v=vs.85))的屬性對應。 `Session.h`包含[會話屬性](/previous-versions/windows/desktop/ms714221(v=vs.85))的屬性對應。 資料列集和命令物件位於單一標頭檔中，稱為*專案名稱*RS. h。 這些屬性是資料列[集屬性](/previous-versions/windows/desktop/ms711252(v=vs.85))群組的成員。

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
