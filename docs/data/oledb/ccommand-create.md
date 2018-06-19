---
title: 'Ccommand:: Create |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CCommand.Create
- CCommand::Create
dev_langs:
- C++
helpviewer_keywords:
- Create method [C++]
ms.assetid: e4bede7a-68bd-491a-97f4-89b03d45cd24
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f85cfd9ed9938d76c28449fae01a87d3bb81a293
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095244"
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
  
## <a name="see-also"></a>另請參閱  
 [CCommand 類別](../../data/oledb/ccommand-class.md)