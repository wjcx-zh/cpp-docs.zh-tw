---
title: 提供者精靈產生的檔案
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB providers, wizard-generated files
ms.assetid: 6e1ac94b-eb90-4abf-82b3-06944b947ebc
ms.openlocfilehash: de5c9056402cb1db25240772eb3c592523daafae
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525327"
---
# <a name="provider-wizard-generated-files"></a>提供者精靈產生的檔案

::: moniker range="vs-2019"

Visual Studio 2019 及更新版本中未提供 ATL OLE DB 提供者精靈。

::: moniker-end

::: moniker range="vs-2017"

**ATL OLE DB 提供者精靈**會產生下列檔案。 下列主題所使用的簡短名稱為 *Custom*，但確切的檔案名稱取決於您在建立提供者時所做的選擇。

|檔案名稱|說明|
|---------------|-----------------|
|*Custom*RS.cpp|包含命令協助程式 `Execute` 方法和提供者資料行對應。|
|*Custom*DS.h|實作資料來源物件。 此標頭檔包含資料來源屬性的屬性對應。|
|*Custom*RS.h|實作命令和資料列集物件。 此標頭檔包含資料列集和命令屬性的屬性對應。|
|*Custom*Sess.h|實作工作階段物件。 此標頭檔包含工作階段屬性的屬性對應。|
|*Custom*.rgs|包含 **OLE DB 提供者精靈**所產生的已註冊物件。|

::: moniker-end

## <a name="see-also"></a>另請參閱

[建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)<br/>
