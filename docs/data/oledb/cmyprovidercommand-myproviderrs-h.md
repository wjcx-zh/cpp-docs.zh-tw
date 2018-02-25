---
title: "CMyProviderCommand (MyProviderRS.H) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cmyprovidercommand
- myproviderrs.h
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderCommand class in MyProviderRS.H
ms.assetid: b30b956e-cc91-4cf5-9fe6-f8b1ce9cc2a5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fe0852b619dc89df4ab9a04f2e7dcbac5d308fce
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="cmyprovidercommand-myproviderrsh"></a>CMyProviderCommand (MyProviderRS.H)
`CMyProviderCommand`類別是提供者命令物件的實作。 它提供的實作`IAccessor`， `ICommandText`，和**ICommandProperties**介面。 `IAccessor`介面是一個資料列集相同。 命令物件會使用存取子，指定繫結參數。 資料列集物件會使用它們來指定繫結的輸出資料行。 `ICommandText`介面是有用的方式，指定的命令加 1。 這個範例會使用`ICommandText`稍後介面時，它會加入自訂程式碼; 它也會覆寫`ICommand::Execute`方法。 **ICommandProperties**介面會處理所有命令和資料列集物件的屬性。  
  
```  
// CMyProviderCommand  
class ATL_NO_VTABLE CMyProviderCommand :   
class ATL_NO_VTABLE CMyProviderCommand :   
   public CComObjectRootEx<CComSingleThreadModel>,  
   public IAccessorImpl<CMyProviderCommand>,  
   public ICommandTextImpl<CMyProviderCommand>,  
   public ICommandPropertiesImpl<CMyProviderCommand>,  
   public IObjectWithSiteImpl<CMyProviderCommand>,  
   public IConvertTypeImpl<CMyProviderCommand>,  
   public IColumnsInfoImpl<CMyProviderCommand>  
```  
  
 `IAccessor`介面會管理使用中命令和資料列集的所有繫結。 取用者可以呼叫**iaccessor:: Createaccessor**的陣列**DBBINDING**結構。 每個**DBBINDING**結構包含資料行繫結應該如何處理 （例如類型和長度） 的相關資訊。 提供者會接收此結構，並接著會判斷應該傳送之資料的方式，以及是否需要任何轉換。 `IAccessor`命令物件中使用介面來處理命令中的任何參數。  
  
 命令物件也會提供的實作`IColumnsInfo`。 OLE DB 需要`IColumnsInfo`介面。 介面可讓取用者來擷取命令的參數的相關資訊。 資料列集物件會使用`IColumnsInfo`介面，以提供者傳回的輸出資料行的相關資訊。  
  
 提供者也包含稱為介面`IObjectWithSite`。 `IObjectWithSite`介面 ATL 2.0 中已實作，並可讓實作器決定將與其本身相關的資訊傳遞給它的子系。 命令物件會使用`IObjectWithSite`資訊來判斷任何產生資料列集物件，關於建立者是誰。  
  
## <a name="see-also"></a>請參閱  
 [提供者精靈產生的檔案](../../data/oledb/provider-wizard-generated-files.md)