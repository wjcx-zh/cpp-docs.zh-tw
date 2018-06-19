---
title: CDaoWorkspaceInfo 結構 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoWorkspaceInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoWorkspaceInfo structure [MFC]
- DAO (Data Access Objects), Workspaces collection
ms.assetid: a1f4b25e-f9c6-4196-b075-d1df99c54124
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd6979124916e8a9cc1dc723008491bababc0322
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366287"
---
# <a name="cdaoworkspaceinfo-structure"></a>CDaoWorkspaceInfo 結構
`CDaoWorkspaceInfo`結構包含定義資料存取物件 (DAO) 資料庫存取的工作區的相關資訊。  
  
## <a name="syntax"></a>語法  
  
```  
struct CDaoWorkspaceInfo  
{  
    CString m_strName;           // Primary  
    CString m_strUserName;       // Secondary  
    BOOL m_bIsolateODBCTrans;    // All  
};  
```  
  
#### <a name="parameters"></a>參數  
 `m_strName`  
 唯一命名工作區中的物件。 若要直接擷取這個屬性的值，呼叫 recordset 物件的[GetName](../../mfc/reference/cdaoquerydef-class.md#getname)成員函式。 如需詳細資訊，請參閱本主題說明 DAO 中的 「 名稱屬性 」。  
  
 *m_strUserName*  
 值，表示工作區中物件的擁有者。 如需相關資訊，請參閱主題 DAO [說明] 中的 「 使用者名稱屬性 」。  
  
 *m_bIsolateODBCTrans*  
 值，指出是否牽涉到相同的 ODBC 資料庫的多筆交易都已隔離。 如需詳細資訊，請參閱[CDaoWorkspace::SetIsolateODBCTrans](../../mfc/reference/cdaoworkspace-class.md#setisolateodbctrans)。 如需相關資訊，請參閱主題 DAO [說明] 中的 < IsolateODBCTrans 屬性 >。  
  
## <a name="remarks"></a>備註  
 工作區是類別的物件[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)。 參考主要、 次要資料庫，且所有上述表示所傳回的資訊是如何[GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo)類別中的成員函式`CDaoWorkspace`。  
  
 所擷取的資訊[CDaoWorkspace::GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo)成員函式會儲存在`CDaoWorkspaceInfo`結構。 `CDaoWorkspaceInfo` 也會定義`Dump`成員函式在偵錯組建。 您可以使用`Dump`來傾印的內容`CDaoWorkspaceInfo`物件。  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdao.h  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDaoWorkspace 類別](../../mfc/reference/cdaoworkspace-class.md)
