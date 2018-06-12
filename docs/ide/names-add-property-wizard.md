---
title: 新增屬性精靈、名稱 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.prop.overview
dev_langs:
- C++
ms.assetid: 0453b7ea-89cb-41a1-80a2-d45f61589c0a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 17c3fd5cfc86f76fcdc1c301bd92bb1fdfac3b9c
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "33339562"
---
# <a name="names-add-property-wizard"></a>名稱、加入屬性精靈
使用此精靈將屬性新增至介面。  
  
 **屬性類型**  
 設定您要新增之屬性的類型。 針對 MFC 分配介面 (Dispinterface)，提供您自己的類型，或從預先定義的清單中選取。 如果您提供屬性的內建實作，[屬性類型] 會設定為內建類型，而且無法變更。  
  
 **屬性名稱**  
 設定屬性的名稱。 針對與 ActiveX 控制項建立關聯的 MFC 分配介面 (Dispinterface)，您可以提供自己的名稱，或從預先定義的清單中選取內建屬性名稱。 如果您提供自己的屬性名稱，[內建] 實作類型無法使用。 如需清單中屬性的描述，請參閱[內建屬性](../ide/stock-properties.md)。  
  
|介面類型|描述|  
|--------------------|-----------------|  
|ATL 雙重介面、自訂介面和本機自訂介面|提供屬性名稱。|  
|MFC 分配介面 (Dispinterface)、MFC ActiveX 控制項分配介面 (Dispinterface)|提供屬性名稱，或從清單中選取內建屬性。 如果您從清單中選取屬性，[屬性類型] 方塊中會顯示適當的值。 根據您在 [實作類型] 下的選擇，您可以變更此類型。|  
  
 **傳回類型**  
 僅限 ATL 介面。 設定屬性的傳回型別。 若是雙重介面，傳回型別一律是 `HRESULT`，而且此方塊無法使用。 若是自訂介面，您可以從清單中選取傳回型別。 仍建議使用 `HRESULT`，因為它提供傳回錯誤的標準方式。  
  
 **變數名稱**  
 僅限 MFC 分配介面 (Dispinterface)。 只有在 [實作類型] 下指定 [成員變數] 時，才可以使用。 設定與屬性建立關聯之成員變數的名稱。 根據預設，變數名稱會設定為 m_*PropertyName*。 您可以編輯此名稱。  
  
 **通知函式**  
 僅限 MFC 分配介面 (Dispinterface)。 只有在 [實作類型] 下指定 [成員變數] 時，才可以使用。 設定屬性變更時所呼叫之通知函式的名稱。 根據預設，通知函式的名稱會設定為 On*PropertyName*Changed。 您可以編輯此名稱。  
  
 **Get 函式**  
 適用於 MFC 分配介面 (Dispinterface)。 只有在 [實作類型] 下指定 [Get/Set 方法] 時，才可以使用。 設定要取得屬性之函式的名稱。 根據預設，Get 函式的名稱會設定為 Get*PropertyName*。 您可以編輯此名稱。 如果您刪除名稱，則會將函式 [GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported) 插入介面分派對應。 Get*PropertyName* 函式指定屬性為可讀取。  
  
 **Set 函式**  
 僅限 MFC 分配介面 (Dispinterface)。 只有在 [實作類型] 下指定 [Get/Set 方法] 時，才可以使用。 設定要設定屬性之函式的名稱。 根據預設，Set 函式的名稱會設定為 Set*PropertyName*。 您可以編輯此名稱。 如果您刪除名稱，則會將函式 [SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported) 插入介面分派對應。 Set*PropertyName* 函式指定屬性為可寫入。  
  
 **實作類型**  
 僅限 MFC 分配介面 (Dispinterface)。 指定如何實作您要新增的屬性。  
  
|實作類型|描述|  
|-------------------------|-----------------|  
|**內建**|為 [屬性名稱] 中選取的屬性指定內建實作。 預設值。 如需詳細資訊，請參閱[內建屬性](../ide/stock-properties.md)。<br /><br /> 如果您指定 [內建]，則 [屬性類型]、[參數類型] 和 [參數名稱] 都會呈暗灰色。|  
|**成員變數**|指定屬性已新增為成員變數。 您可以新增自訂屬性或大多數內建屬性作為成員變數。 您無法指定 **Caption**、**hWnd** 和 **Text** 屬性的 [成員變數]。<br /><br /> 在 [變數名稱] 和 [通知函式] 下提供預設名稱。 您可以編輯此名稱。|  
|**Get/Set 方法**|指定屬性預設已新增為 Get*PropertyName* 和 Set*PropertyName* 函式。 這些名稱會出現在 [Get 函式] 和 [Set 函式] 下。<br /><br /> 您可以變更預設的 [屬性類型]，這會傳遞 Get 函式的值。 您可以指定 **Get** 和 `Set` 函式的參數。|  
  
 **Get 函式**  
 適用於 ATL 介面。 將屬性設定為可讀取；也就是說，它會建立 **Get** 方法，以從物件擷取這個屬性。 您必須選取 **Get**、`Put` 或兩者。  
  
 **Put 函式**  
 僅限 ATL 介面。 將屬性設定為可寫入；也就是說，它會建立 `Put` 方法，以設定或「放置」物件的這個屬性。 您必須選取 **Get**、`Put` 或兩者。 如果您選取此選項，您可以選擇下列兩個方式來實作方法：  
  
|選項|描述|  
|------------|-----------------|  
|**PropPut**|[PropPut](../windows/propput.md) 函式會傳回物件的複本。 這是預設值，而且是將屬性設為可寫入的最常見方式。|  
|**PropPutRef**|[PropPutRef](../windows/propputref.md) 函式會傳回物件的參考，而不是傳回物件本身的複本。 請考慮針對大型結構或陣列等物件使用此選項，這類物件可能會有初始設定額外負荷。|  
  
 **參數屬性**  
 僅限 ATL 介面。 設定 [參數名稱] 所指定的參數是 **in**、**out**、兩者或無。  
  
|選項|描述|  
|------------|-----------------|  
|**in**|表示參數會從呼叫程序傳遞至被呼叫程序。|  
|**out**|表示指標參數會從被呼叫程序傳回至呼叫程序 (從伺服器至用戶端)。|  
  
 **參數類型**  
 設定參數的資料類型。 請從清單中選取類型。  
  
 **參數名稱**  
 如果屬性具有參數，請設定您要為屬性新增之參數的名稱。 按一下 [新增] 之後，參數名稱會出現在 [參數清單] 中。  
  
 **參數清單**  
 顯示要新增至屬性 (Property) 的屬性 (Attribute) 清單。 清單中的每個項目是由參數名稱、參數類型和屬性所組成。 使用 [新增] 和 [移除] 更新清單。  
  
 **[新增]**  
 將您在 [參數名稱] 和 [參數類型] 中指定的參數新增至 [參數清單]。 您必須按一下 [新增]，才能將參數新增至清單。  
  
 **移除**  
 移除您在 [參數清單] 中選取的參數。  
  
 **預設屬性**  
 僅限 MFC 分配介面 (Dispinterface)。 將此屬性設定為介面的預設值。 一個介面只能有一個預設屬性；指定預設屬性之後，對於您新增至介面的任何其他屬性，此方塊無法使用。  
  
## <a name="see-also"></a>請參閱  
 [新增屬性](../ide/adding-a-property-visual-cpp.md)   
 [新增屬性精靈、IDL 屬性](../ide/idl-attributes-add-property-wizard.md)   
 [實作介面](../ide/implementing-an-interface-visual-cpp.md)