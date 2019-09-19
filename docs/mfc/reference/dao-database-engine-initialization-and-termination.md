---
title: DAO 資料庫引擎初始化及終止
ms.date: 09/17/2019
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
ms.openlocfilehash: ccdf2e7b0f31576dddccad016e6b32806cdb82bf
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095881"
---
# <a name="dao-database-engine-initialization-and-termination"></a>DAO 資料庫引擎初始化及終止

DAO 會與 Access 資料庫搭配使用，並透過 Office 2013 支援。 3.6 是最終版本，並被視為已淘汰。 使用 MFC DAO 物件時，必須在應用程式或 DLL 退出前先初始化然後終止 DAO 資料庫引擎。 `AfxDaoInit` 和 `AfxDaoTerm` 這兩個函式會執行這些工作。

### <a name="dao-database-engine-initialization-and-termination"></a>DAO 資料庫引擎初始化及終止

|||
|-|-|
|[AfxDaoInit](#afxdaoinit)|初始化 DAO 資料庫引擎。|
|[AfxDaoTerm](#afxdaoterm)|終止 DAO 資料庫引擎。|

##  <a name="afxdaoinit"></a>  AfxDaoInit

此函式會初始化 DAO 資料庫引擎。

```

void AfxDaoInit();

throw(CDaoException*);
```

### <a name="remarks"></a>備註

在大部分的情況下，您不需要`AfxDaoInit`呼叫，因為應用程式會在需要時自動呼叫它。

如需相關資訊，以及呼叫`AfxDaoInit`的範例，請參閱[技術提示 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

### <a name="requirements"></a>需求

  **標頭**afxdao。h

##  <a name="afxdaoterm"></a>  AfxDaoTerm

此函式會終止 DAO 資料庫引擎。

```

void AfxDaoTerm();
```

### <a name="remarks"></a>備註

一般來說，您只需要在一般的 MFC DLL 中呼叫此函式;應用程式會在需要`AfxDaoTerm`時自動呼叫。

在一般的`ExitInstance` mfc dll 中`AfxDaoTerm` ，請在函式之前呼叫，但在終結所有 MFC DAO 物件之後。

如需相關資訊，請參閱[技術提示 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

### <a name="requirements"></a>需求

  **標頭**afxdao。h

## <a name="see-also"></a>另請參閱

[宏和全域](../../mfc/reference/mfc-macros-and-globals.md)
