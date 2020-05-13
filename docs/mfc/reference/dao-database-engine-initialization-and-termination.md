---
title: DAO 資料庫引擎初始化及終止
ms.date: 09/17/2019
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
ms.openlocfilehash: 62460e8e55f70b8cb0743f1d044636d25121050d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365898"
---
# <a name="dao-database-engine-initialization-and-termination"></a>DAO 資料庫引擎初始化及終止

DAO 與 Access 資料庫一起使用,並通過 Office 2013 支援。 DAO 3.6 是最終版本,它被視為過時版本。 使用 MFC DAO 物件時，必須在應用程式或 DLL 退出前先初始化然後終止 DAO 資料庫引擎。 `AfxDaoInit` 和 `AfxDaoTerm` 這兩個函式會執行這些工作。

### <a name="dao-database-engine-initialization-and-termination"></a>DAO 資料庫引擎初始化及終止

|||
|-|-|
|[AfxDaoInit](#afxdaoinit)|初始化 DAO 資料庫引擎。|
|[AfxDaoTerm](#afxdaoterm)|終止 DAO 資料庫引擎。|

## <a name="afxdaoinit"></a><a name="afxdaoinit"></a>阿FXDaoinit

此功能初始化 DAO 資料庫引擎。

```

void AfxDaoInit();

throw(CDaoException*);
```

### <a name="remarks"></a>備註

在大多數情況下,您不需要調用`AfxDaoInit`,因為應用程式在需要時會自動調用它。

有關相關資訊,以及調用`AfxDaoInit`的範例,請參閱[技術說明 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

### <a name="requirements"></a>需求

  **標題**afxdao.h

## <a name="afxdaoterm"></a><a name="afxdaoterm"></a>阿FXDaoterm

此函數終止 DAO 資料庫引擎。

```

void AfxDaoTerm();
```

### <a name="remarks"></a>備註

通常,您只需要在常規 MFC DLL 中調用此函數;否則,只需在常規 MFC DLL 中調用此函數。應用程式在需要時自動呼叫`AfxDaoTerm`。

在常規 MFC`AfxDaoTerm`DLL 中`ExitInstance`,在函數之前調用,但之後所有 MFC DAO 物件已銷毀。

有關相關信息,請參閱[技術說明 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

### <a name="requirements"></a>需求

  **標題**afxdao.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
