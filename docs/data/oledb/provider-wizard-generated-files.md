---
title: "提供者精靈產生的檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
ms.assetid: 6e1ac94b-eb90-4abf-82b3-06944b947ebc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9cfcce4242cf985b8ffa50b9df234d609cfe7f3f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="provider-wizard-generated-files"></a>提供者精靈產生的檔案
ATL OLE DB 提供者精靈會產生下列檔案。 下列主題會使用簡短名稱"MyProvider"，但是實際的檔案名稱取決於建立提供者時所做的選擇。  
  
|檔案名稱|描述|  
|---------------|-----------------|  
|MyProviderRS.cpp|包含命令 helper`Execute`方法，並提供者資料行對應。|  
|MyProviderDS.h|實作資料來源物件。 此標頭檔會包含資料來源屬性的屬性對應。|  
|MyProviderRS.h|實作命令和資料列集物件。 此標頭檔包含的屬性對應資料列集和命令屬性。|  
|MyProviderSess.h|實作的工作階段物件。 此標頭檔包含工作階段屬性的屬性對應。|  
|MyProvider.rgs|包含已註冊的物件 OLE DB 提供者精靈所產生。|  
  
## <a name="see-also"></a>請參閱  
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)