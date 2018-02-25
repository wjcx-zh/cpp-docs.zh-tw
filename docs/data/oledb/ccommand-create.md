---
title: "Ccommand:: Create |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCommand.Create
- CCommand::Create
dev_langs:
- C++
helpviewer_keywords:
- Create method [C++]
ms.assetid: e4bede7a-68bd-491a-97f4-89b03d45cd24
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 113d1e67197dd85acbec7ccffb93a3be7537d679
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="ccommandcreate"></a>CCommand::Create
呼叫[ccommand:: Createcommand](../../data/oledb/ccommand-createcommand.md)建立命令指定的工作階段，然後呼叫[icommandtext:: Setcommandtext](https://msdn.microsoft.com/en-us/library/ms709825.aspx)指定的命令文字。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT CCommandBase::Create(const CSession& session,   
   LPCWSTR wszCommand,   
   REFGUID guidCommand = DBGUID_DEFAULT) throw ();  


HRESULT CCommandBase::Create(const CSession& session,   
   LPCSTR szCommand,   
   REFGUID guidCommand = DBGUID_DEFAULT) throw ();  
```  
  
#### <a name="parameters"></a>參數  
 `session`  
 [in]建立命令所在的工作階段。  
  
 `wszCommand`  
 [in]命令字串的 Unicode 文字指標。  
  
 `szCommand`  
 [in]ANSI 文字，為命令字串的指標。  
  
 `guidCommand`  
 [in]剖析命令文字中指定的語法和一般的規則，若要使用的提供者的 GUID。 如需方言的說明，請參閱[ICommandText::GetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx)中*OLE DB 程式設計人員參考*。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 第一種形式的**建立**採用 Unicode 命令字串。 第二種**建立**採用 ANSI 命令字串 （提供與現有的 ANSI 應用程式的回溯相容性）。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CCommand 類別](../../data/oledb/ccommand-class.md)