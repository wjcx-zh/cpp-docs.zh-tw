---
title: 資料成員屬性 (c + + COM) |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- data members [C++], attributes
- data members [C++]
ms.assetid: 95b2397d-1daf-4ae4-8cd0-06956d005b13
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5019503bed9dd0012d8aafc1ade4abd3107335ac
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790690"
---
# <a name="data-member-attributes"></a>資料成員屬性

下列屬性套用至類別、 coclass 或介面中的資料成員。

|屬性|描述|
|---------------|-----------------|
|[db_accessor](db-accessor.md)|群組`db_column`參與屬性`IAccessor`為基礎的繫結。|
|[db_column](db-column.md)|將指定的資料行的資料列集繫結。|
|[db_command](db-command.md)|建立 OLE DB 命令。|
|[db_param](db-param.md)|關聯的輸入或輸出參數中指定的成員變數，並分隔的變數。|
|[db_source](db-source.md)|建立資料來源的連接。|
|[db_table](db-table.md)|開啟 OLE DB 資料表。|
|[defaultbind](defaultbind.md)|表示最能代表物件的單一、 可繫結屬性。|
|[displaybind](displaybind.md)|指出應該顯示給使用者，作為可繫結的屬性。|
|[id](id.md)|指定成員函式 （屬性或方法，在介面或 dispinterface） 的 DISPID。|
|[範圍](range-cpp.md)|指定引數或在執行階段設定其值的欄位的允許值的範圍。|
|[rdx](rdx.md)|建立登錄機碼或修改現有的登錄機碼。|
|[readonly](readonly-cpp.md)|禁止指派給資料成員。|
|[requestedit](requestedit.md)|表示屬性支援`OnRequestEdit`通知。|

## <a name="see-also"></a>另請參閱

[依使用方式分類的屬性](attributes-by-usage.md)