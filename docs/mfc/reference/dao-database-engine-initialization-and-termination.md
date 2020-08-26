---
title: DAO 資料庫引擎初始化及終止
ms.date: 09/17/2019
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
ms.openlocfilehash: 0a70dd396a87315a96224edccf13250a2927cd99
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837589"
---
# <a name="dao-database-engine-initialization-and-termination"></a>DAO 資料庫引擎初始化及終止

DAO 可搭配 Access 資料庫使用，並透過 Office 2013 支援。 DAO 3.6 是最終版本，且會被視為已淘汰。 使用 MFC DAO 物件時，必須在應用程式或 DLL 退出前先初始化然後終止 DAO 資料庫引擎。 `AfxDaoInit` 和 `AfxDaoTerm` 這兩個函式會執行這些工作。

### <a name="dao-database-engine-initialization-and-termination"></a>DAO 資料庫引擎初始化及終止

|名稱|描述|
|-|-|
|[AfxDaoInit](#afxdaoinit)|初始化 DAO 資料庫引擎。|
|[AfxDaoTerm](#afxdaoterm)|終止 DAO 資料庫引擎。|

## <a name="afxdaoinit"></a><a name="afxdaoinit"></a> AfxDaoInit

此函式會初始化 DAO 資料庫引擎。

```

void AfxDaoInit();

throw(CDaoException*);
```

### <a name="remarks"></a>備註

在大多數情況下，您不需要呼叫， `AfxDaoInit` 因為應用程式會在需要時自動呼叫它。

如需相關資訊，以及呼叫的範例 `AfxDaoInit` ，請參閱 [技術附注 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdao。h

## <a name="afxdaoterm"></a><a name="afxdaoterm"></a> AfxDaoTerm

此函式會終止 DAO 資料庫引擎。

```

void AfxDaoTerm();
```

### <a name="remarks"></a>備註

一般而言，您只需要在一般 MFC DLL 中呼叫此函式;應用程式會 `AfxDaoTerm` 在需要時自動呼叫。

在一般 MFC Dll 中，呼叫函式 `AfxDaoTerm` 之前的 `ExitInstance` ，但在所有 MFC DAO 物件都已終結之後。

如需相關資訊，請參閱 [技術附注 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

### <a name="requirements"></a>規格需求

  **標頭** afxdao。h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
