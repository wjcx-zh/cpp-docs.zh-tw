---
title: "ICommandTarget 介面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ICommandTarget
- AFXWINFORMS/ICommandTarget
- AFXWINFORMS/ICommandTarget::Initialize
dev_langs:
- C++
helpviewer_keywords:
- ICommandTarget interface
ms.assetid: dd9927f6-3479-4e7c-8ef9-13206cf901f3
caps.latest.revision: 27
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 825fde18c56afb91bdb469212817109dc35abf68
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="icommandtarget-interface"></a>ICommandTarget 介面
使用者控制項提供介面來接收命令來源物件的命令。  
  
## <a name="syntax"></a>語法  
  
```  
interface class ICommandTarget  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[ICommandTarget::Initialize](#initialize)|初始化命令目標物件。|  
  
## <a name="remarks"></a>備註  
 當您將使用者控制項裝載在 MFC 檢視中， [CWinFormsView](../../mfc/reference/cwinformsview-class.md)路由命令，並更新命令 UI 至使用者控制項中的郵件，讓它處理 MFC 命令 （例如，框架的功能表項目和工具列按鈕）。 藉由實作`ICommandTarget`，讓使用者控制項的參考[ICommandSource](../../mfc/reference/icommandsource-interface.md)物件。  
  
 請參閱[How to︰ 將命令傳送至 Windows Form 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)如需如何使用`ICommandTarget`。  
  
 如需有關如何使用 Windows Form 的詳細資訊，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxwinforms.h （定義於組件 atlmfc\lib\mfcmifc80.dll）  
  
##  <a name="initialize"></a>ICommandTarget::Initialize  
 初始化命令目標物件。  
  
```  
void Initialize(ICommandSource^ cmdSource);  
```  
  
### <a name="parameters"></a>參數  
 `cmdSource`  
 命令來源物件的控制代碼。  
  
### <a name="remarks"></a>備註  
 當您裝載在 MFC 檢視的使用者控制項時，CWinFormsView 會將命令和更新命令 UI 訊息路由至使用者控制項，以允許它處理 MFC 命令。  
  
 這個方法會初始化命令目標物件，並將它與指定的命令來源物件 cmdSource 關聯。 使用者控制項類別實作中，應該呼叫它。 在初始化時，應該向命令來源物件的初始化實作中呼叫 ICommandSource::AddCommandHandler 註冊命令處理常式。 請參閱 < 如何︰ 新增命令傳送至 Windows Form 控制項，如需如何執行這項操作時，用於初始化的範例。  
  
## <a name="see-also"></a>另請參閱  
 [如何︰ 新增命令傳送至 Windows Form 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)   
 [ICommandSource 介面](../../mfc/reference/icommandsource-interface.md)




