---
title: DEFINE_COMMAND_EX |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- DEFINE_COMMAND_EX
dev_langs:
- C++
helpviewer_keywords:
- DEFINE_COMMAND_EX macro
ms.assetid: d3e2ef20-1455-46d2-8499-8ab84bbb90a4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b2a77fa0d6655edeee88df3c7c45e1936a766b40
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101038"
---
# <a name="definecommandex"></a>DEFINE_COMMAND_EX
指定將用來建立資料列集，使用時的命令[CCommand](../../data/oledb/ccommand-class.md)類別。 支援 Unicode 和 ANSI 應用程式。  
  
## <a name="syntax"></a>語法  
  
```cpp
DEFINE_COMMAND_EX(x, wszCommand)  
  
```  
  
#### <a name="parameters"></a>參數  
 *x*  
 [in]使用者資料錄 （命令） 類別的名稱。  
  
 `wszCommand`  
 [in]將用來建立資料列集，使用時的命令字串[CCommand](../../data/oledb/ccommand-class.md)。  
  
## <a name="remarks"></a>備註  
 如果您未指定命令文字中的，將做為預設使用您指定的命令字串[ccommand:: Open](../../data/oledb/ccommand-open.md)方法。  
  
 這個巨集接受 Unicode 字串，不論應用程式類型。 這個巨集是透過慣用[DEFINE_COMMAND](../../data/oledb/define-command.md)因為它支援 Unicode 和 ANSI 應用程式。  
  
## <a name="example"></a>範例  
 請參閱[BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md)。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 消費者範本的巨集和全域函式](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)