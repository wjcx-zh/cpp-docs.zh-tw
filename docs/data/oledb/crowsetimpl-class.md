---
title: "CRowsetImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRowsetImpl
- ATL.CRowsetImpl
- ATL::CRowsetImpl
dev_langs: C++
helpviewer_keywords: CRowsetImpl class
ms.assetid: e97614b3-b11d-4806-a0d3-b9401331473f
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1ae1bb857353b72551e4766516c571c0091062d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="crowsetimpl-class"></a>CRowsetImpl 類別
提供標準的 OLE DB 資料列集實作，而不需要許多實作介面的多重繼承。  
  
## <a name="syntax"></a>語法  
  
```  
template <  
   class T,  
   class Storage,  
   class CreatorClass,  
   class ArrayType = CAtlArray<Storage>,   
   class RowClass = CSimpleRow,   
   class RowsetInterface = IRowsetImpl < T, IRowset >   
>  
class CRowsetImpl :    
   public CComObjectRootEx<CreatorClass::_ThreadModel>,   
   public CRowsetBaseImpl<T, Storage, ArrayType, RowsetInterface>,   
   public IRowsetInfoImpl<T, CreatorClass::_PropClass>  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 使用者的類別衍生自`CRowsetImpl`。  
  
 `Storage`  
 使用者記錄類別。  
  
 `CreatorClass`  
 類別包含屬性的資料列集。通常命令。  
  
 `ArrayType`  
 類別，做為資料列集的資料儲存體。 這個參數預設值為`CAtlArray`，但它可以支援必要的功能的任何類別。  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[NameFromDBID](../../data/oledb/crowsetimpl-namefromdbid.md)|擷取從字串**DBID**並將它複製到`bstr`傳入。|  
|[SetCommandText](../../data/oledb/crowsetimpl-setcommandtext.md)|驗證並儲存**DBID**中兩個字串 ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md))。|  
  
### <a name="overridable-methods"></a>可覆寫方法  
  
|||  
|-|-|  
|[GetColumnInfo](../../data/oledb/crowsetimpl-getcolumninfo.md)|擷取特定的用戶端要求的資料行資訊。|  
|[GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md)|如果任一個或兩個參數包含字串值，而且如果是，檢查複製的字串值資料成員[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。|  
|[ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md)|檢查是否有任一個或兩個**DBID**s 包含字串值，而且如果是的話，會將它們複製到其資料成員[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)和[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|[m_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md)|根據預設，`CAtlArray`上的使用者資料錄的樣板引數，templatizes `CRowsetImpl`。 變更也可以使用另一個陣列型別類別`ArrayType`的樣板引數`CRowsetImpl`。|  
|[m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md)|包含資料列集的初始命令。|  
|[m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)|包含資料列集的起始索引。|  
  
## <a name="remarks"></a>備註  
 `CRowsetImpl`提供靜態向上轉型成為表單中的覆寫。 方法會控制在其中指定的資料列集將會驗證命令文字的方式。 您可以建立自己`CRowsetImpl`-樣式藉由實作介面多重繼承的類別。 唯一的方法，您必須提供實作**Execute**。 根據您建立哪種類型的資料列集，creator 方法將會針對不同的簽章**Execute**。 例如，如果您使用`CRowsetImpl`-衍生類別來實作結構描述資料列**Execute**方法會有下列簽章：  
  
 `HRESULT Execute(LONG* pcRows, ULONG cRestrictions, const VARIANT* rgRestrictions)`  
  
 如果您要建立`CRowsetImpl`-衍生類別來實作的命令或工作階段的資料列集， **Execute**方法會有下列簽章：  
  
 `HRESULT Execute(LONG* pcRows, DBPARAMS* pParams)`  
  
 若要實作的任何`CRowsetImpl`-衍生**Execute**方法，您必須填入您的內部資料緩衝區 ([m_rgRowData](../../data/oledb/crowsetimpl-m-rgrowdata.md))。  
  
## <a name="requirements"></a>需求  
 **Header:** atldb.h