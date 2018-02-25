---
title: "DEFINE_COMMAND |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- DEFINE_COMMAND
dev_langs:
- C++
helpviewer_keywords:
- DEFINE_COMMAND macro
ms.assetid: 9d724968-e242-413c-9a13-e7175fccf9b1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3af85ea4c223cac4e770dd9b45ffe785309f9f69
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="definecommand"></a>DEFINE_COMMAND
指定將用來建立資料列集，使用時的命令[CCommand](../../data/oledb/ccommand-class.md)類別。 接受只比對指定的應用程式類型 （ANSI 或 Unicode） 字串類型。  
  
> [!NOTE]
>  建議您改用[DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md)而不是`DEFINE_COMMAND`。  
  
## <a name="syntax"></a>語法  
  
```cpp
DEFINE_COMMAND(x, szCommand)  
  
```  
  
#### <a name="parameters"></a>參數  
 *x*  
 [in]使用者資料錄 （命令） 類別的名稱。  
  
 `szCommand`  
 [in]將用來建立資料列集，使用時的命令字串[CCommand](../../data/oledb/ccommand-class.md)。  
  
## <a name="remarks"></a>備註  
 如果您未指定命令文字中的，將做為預設使用您指定的命令字串[ccommand:: Open](../../data/oledb/ccommand-open.md)方法。  
  
 這個巨集接受 ANSI 字串，如果您建置為 ANSI，應用程式或 Unicode 字串，如果您建置應用程式為 Unicode。 建議您改用[DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md)而不是`DEFINE_COMMAND`，因為前者接受 Unicode 字串，不論 ANSI 或 Unicode 應用程式類型。  
  
## <a name="example"></a>範例  
 請參閱[BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md)。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [OLE DB 消費者範本的巨集和全域函式](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)