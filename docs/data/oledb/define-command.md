---
title: DEFINE_COMMAND |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- DEFINE_COMMAND
dev_langs:
- C++
helpviewer_keywords:
- DEFINE_COMMAND macro
ms.assetid: 9d724968-e242-413c-9a13-e7175fccf9b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 51f975b0477d29fbb35880c796f52612456c32c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 消費者範本的巨集和全域函式](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)