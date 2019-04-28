---
title: CDaoWorkspaceInfo 結構
ms.date: 11/04/2016
f1_keywords:
- CDaoWorkspaceInfo
helpviewer_keywords:
- CDaoWorkspaceInfo structure [MFC]
- DAO (Data Access Objects), Workspaces collection
ms.assetid: a1f4b25e-f9c6-4196-b075-d1df99c54124
ms.openlocfilehash: afbc73c079a6deec3f3e1b7455f9f2dbface5025
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62253626"
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

*m_strName*<br/>
唯一命名工作區的物件。 若要直接擷取這個屬性的值，呼叫 recordset 物件的[GetName](../../mfc/reference/cdaoquerydef-class.md#getname)成員函式。 如需詳細資訊，請參閱主題 DAO [說明] 中的 「 名稱屬性 」。

*m_strUserName*<br/>
值，表示工作區中物件的擁有者。 如需相關資訊，請參閱 DAO [說明] 中的 「 使用者名稱屬性 」。

*m_bIsolateODBCTrans*<br/>
值，指出是否包含相同的 ODBC 資料庫的多個交易隔離。 如需詳細資訊，請參閱 < [CDaoWorkspace::SetIsolateODBCTrans](../../mfc/reference/cdaoworkspace-class.md#setisolateodbctrans)。 如需相關資訊，請參閱 DAO [說明] 中的 < IsolateODBCTrans 屬性 >。

## <a name="remarks"></a>備註

工作區是類別的物件[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)。 主要、 次要資料庫，且上述所有的參考會指出所傳回的資訊是如何[GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo)類別中的成員函式`CDaoWorkspace`。

所擷取的資訊[CDaoWorkspace::GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo)成員函式會儲存在`CDaoWorkspaceInfo`結構。 `CDaoWorkspaceInfo` 也會定義`Dump`成員函式，在偵錯組建。 您可以使用`Dump`傾印的內容`CDaoWorkspaceInfo`物件。

## <a name="requirements"></a>需求

**標頭：** afxdao.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoWorkspace 類別](../../mfc/reference/cdaoworkspace-class.md)
