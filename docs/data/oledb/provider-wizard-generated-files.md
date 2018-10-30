---
title: 提供者精靈產生的檔案 |Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
ms.assetid: 6e1ac94b-eb90-4abf-82b3-06944b947ebc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 40422ac7894523a28a2135b7f5005eb1f11d36c8
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216366"
---
# <a name="provider-wizard-generated-files"></a>提供者精靈產生的檔案

**ATL OLE DB 提供者精靈**會產生下列檔案。 下列主題會使用的簡稱*自訂*，但是確切的檔案名稱取決於建立提供者時所做的選擇。

|檔案名稱|描述|
|---------------|-----------------|
|*自訂*RS.cpp|包含命令的協助程式`Execute`方法和提供者的資料行對應。|
|*自訂*DS.h|實作資料來源物件。 此標頭檔包含資料來源屬性的屬性對應。|
|*自訂*RS.h|實作命令和資料列集物件。 此標頭檔包含資料列集和命令屬性的屬性對應。|
|*自訂*Sess.h|實作工作階段物件。 此標頭檔包含工作階段屬性的屬性對應。|
|*自訂*.rgs|包含所產生的已註冊的物件**OLE DB 提供者精靈**。|

## <a name="see-also"></a>另請參閱

[建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)<br/>
