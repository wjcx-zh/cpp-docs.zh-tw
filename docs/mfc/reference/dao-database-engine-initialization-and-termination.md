---
title: DAO 資料庫引擎初始化及終止
ms.date: 09/17/2019
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
ms.openlocfilehash: 24a24d5a81da18d01472fc760c2adf96ee9868d5
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303461"
---
# <a name="dao-database-engine-initialization-and-termination"></a>DAO 資料庫引擎初始化及終止

DAO 會與 Access 資料庫搭配使用，並透過 Office 2013 支援。 DAO 3.6 是最後的版本，被視為已淘汰。 使用 MFC DAO 物件時，必須在應用程式或 DLL 退出前先初始化然後終止 DAO 資料庫引擎。 `AfxDaoInit` 和 `AfxDaoTerm` 這兩個函式會執行這些工作。

### <a name="dao-database-engine-initialization-and-termination"></a>DAO 資料庫引擎初始化及終止

|||
|-|-|
|[AfxDaoInit](#afxdaoinit)|初始化 DAO 資料庫引擎。|
|[AfxDaoTerm](#afxdaoterm)|終止 DAO 資料庫引擎。|

##  <a name="afxdaoinit"></a>AfxDaoInit

此函式會初始化 DAO 資料庫引擎。

```

void AfxDaoInit();

throw(CDaoException*);
```

### <a name="remarks"></a>備註

在大部分情況下，您不需要呼叫 `AfxDaoInit`，因為應用程式會在需要時自動呼叫它。

如需相關資訊，以及呼叫 `AfxDaoInit`的範例，請參閱[技術附注 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

### <a name="requirements"></a>需求

  **標頭**afxdao。h

##  <a name="afxdaoterm"></a>AfxDaoTerm

此函式會終止 DAO 資料庫引擎。

```

void AfxDaoTerm();
```

### <a name="remarks"></a>備註

一般來說，您只需要在一般的 MFC DLL 中呼叫此函式;應用程式會在需要時自動呼叫 `AfxDaoTerm`。

在一般的 MFC Dll 中，請在 `ExitInstance` 函式之前呼叫 `AfxDaoTerm`，但在終結所有 MFC DAO 物件之後。

如需相關資訊，請參閱[技術提示 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

### <a name="requirements"></a>需求

  **標頭**afxdao。h

## <a name="see-also"></a>請參閱

[宏和全域](../../mfc/reference/mfc-macros-and-globals.md)
