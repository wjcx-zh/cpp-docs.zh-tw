---
title: DAO 資料庫引擎初始化及終止
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros.data
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
ms.openlocfilehash: 8ad0c1df2f5b6a7b1b48d2db119b04e4b3234f10
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57297629"
---
# <a name="dao-database-engine-initialization-and-termination"></a>DAO 資料庫引擎初始化及終止

使用 MFC DAO 物件時，必須在應用程式或 DLL 退出前先初始化然後終止 DAO 資料庫引擎。 
  `AfxDaoInit` 和 `AfxDaoTerm` 這兩個函式會執行這些工作。

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

在大部分情況下，您不需要呼叫`AfxDaoInit`因為應用程式會在需要時，會自動呼叫它。

如需相關資訊，以及呼叫的範例`AfxDaoInit`，請參閱 <<c2> [ 技術提示 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

### <a name="requirements"></a>需求

  **標頭**afxdao.h

##  <a name="afxdaoterm"></a>  AfxDaoTerm

此函式會終止 DAO 資料庫引擎。

```

void AfxDaoTerm();
```

### <a name="remarks"></a>備註

一般而言，您只需要在一般 MFC DLL; 呼叫此函式應用程式會自動呼叫`AfxDaoTerm`需要時。

在標準 MFC Dll，呼叫`AfxDaoTerm`之前`ExitInstance`函式，但之後所有的 MFC DAO 物件皆已終結。

如需相關資訊，請參閱[技術提示 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

### <a name="requirements"></a>需求

  **標頭**afxdao.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
