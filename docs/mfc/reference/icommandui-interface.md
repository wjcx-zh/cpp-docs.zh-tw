---
title: "ICommandUI 介面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ICommandUI
- AFXWINFORMS/ICommandUI
- AFXWINFORMS/icommandui__Check
- AFXWINFORMS/ICommandUI::ContinueRouting
- AFXWINFORMS/ICommandUI::Enabled
- AFXWINFORMS/ICommandUI::ID
- AFXWINFORMS/ICommandUI::Index
- AFXWINFORMS/ICommandUI::Radio
- AFXWINFORMS/ICommandUI::Text
dev_langs:
- C++
helpviewer_keywords:
- ICommandUI interface
ms.assetid: 134afe8d-dcdf-47ca-857a-a166a6b665dd
caps.latest.revision: 24
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 1db6b3fa58639140322816c37103566353b15633
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="icommandui-interface"></a>ICommandUI 介面
管理使用者介面的命令。  
  
## <a name="syntax"></a>語法  
  
```  
interface class ICommandUI  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[icommandui__Check](#check)|將此命令的使用者介面項目設定為適當的核取狀態。|  
|[ICommandUI::ContinueRouting](#continuerouting)|會告知命令路由機制，繼續傳送處理常式的鏈結中向下目前的訊息。|  
|[ICommandUI::Enabled](#enabled)|啟用或停用使用者介面項目，此命令。|  
|[ICommandUI::ID](#id)|取得所表示的使用者介面物件的 ID`ICommandUI`物件。|  
|[ICommandUI::Index](#index)|取得所表示的使用者介面物件的索引`ICommandUI`物件。|  
|[ICommandUI::Radio](#radio)|將此命令的使用者介面項目設定為適當的核取狀態。|  
|[ICommandUI::Text](#text)|設定使用者介面項目，此命令的文字。|  
  
## <a name="remarks"></a>備註  
 這個介面會提供方法和屬性，以管理使用者介面的命令。 `ICommandUI`類似於[CCmdUI 類別](../../mfc/reference/ccmdui-class.md)，只不過`ICommandUI`用於與.NET 元件相互操作的 MFC 應用程式。  
  
 `ICommandUI`用於`ON_UPDATE_COMMAND_UI`中的處理常式[ICommandTarget](../../mfc/reference/icommandtarget-interface.md)-衍生的類別。 當應用程式的使用者啟動 （選取或按下滑鼠） 功能表上，每個功能表項目會顯示為已啟用或停用。 每個功能表命令的目標是提供這項資訊藉由實作`ON_UPDATE_COMMAND_UI`處理常式。 每個命令的使用者介面物件，在應用程式中，使用 [屬性] 視窗來建立訊息對應項目和每個處理常式的函式原型。  
  
 如需有關如何`ICommandUI`介面用在命令路由，請參閱[How to︰ 將命令傳送至 Windows Form 控制項](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)。  
  
 如需有關如何使用 Windows Form 的詳細資訊，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
 如需有關使用者介面的命令在 MFC 中的管理方式的詳細資訊，請參閱[CCmdUI 類別](../../mfc/reference/ccmdui-class.md)。  
  
## <a name="check"></a>ICommandUI::Check  
將此命令的使用者介面項目設定為適當的核取狀態。
```
property UICheckState Check;
```
## <a name="remarks"></a>備註  
此屬性設定為適當的核取狀態的使用者介面項目，此命令。 核取設為下列值︰  
- 0 取消核取  
- 1 檢查  
- 不確定設定&2;  

## <a name="continuerouting"></a>ICommandUI::ContinueRouting   
會告知命令路由機制，繼續傳送處理常式的鏈結中向下目前的訊息。
```
void ContinueRouting();
```
## <a name="remarks"></a>備註
這是進階的成員函式應該會傳回 FALSE ON_COMMAND_EX 處理常式的搭配使用。 如需詳細資訊，請參閱技術附註 TN006︰ 訊息對應。

## <a name="enabled"></a>ICommandUI::Enabled 
啟用或停用使用者介面項目，此命令。
```
property bool Enabled;
```
## <a name="remarks"></a>備註
這個屬性會啟用或停用使用者介面項目，此命令。 設定 啟用，以 true，讓項目，為 false，則將它停用。

## <a name="id"></a>ICommandUI::ID  
取得 ICommandUI 物件所代表的使用者介面物件的識別碼。
```
property unsigned int ID;
```
## <a name="remarks"></a>備註
這個屬性會取得功能表項目、 工具列按鈕或其他 ICommandUI 物件所代表的使用者介面物件的識別碼 （處理）。

## <a name="index"></a>ICommandUI::Index   
取得 ICommandUI 物件所代表的使用者介面物件的索引。
```
property unsigned int Index;
```
## <a name="remarks"></a>備註
這個屬性會取得功能表項目、 工具列按鈕或其他 ICommandUI 物件所代表的使用者介面物件的索引 （處理）。

## <a name="radio"></a>ICommandUI::Radio 
將此命令的使用者介面項目設定為適當的核取狀態。
```
property bool Radio;
```
## <a name="remarks"></a>備註
此屬性設定為適當的核取狀態的使用者介面項目，此命令。 如果為 true 則啟用項目; 設定電台否則為 FALSE。

## <a name="text"></a>ICommandUI::Text 
設定使用者介面項目，此命令的文字。
```
property String^ Text;
```
## <a name="remarks"></a>備註
這個屬性設定的使用者介面項目，此命令的文字。 設定文字的文字字串控制代碼。

## <a name="requirements"></a>需求  
 **標頭︰** afxwinforms.h （定義於組件 atlmfc\lib\mfcmifc80.dll）  
  
## <a name="see-also"></a>另請參閱  
 [CCmdUI 類別](../../mfc/reference/ccmdui-class.md)

