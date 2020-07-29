---
title: 新增屬性
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.prop.overview
- vc.codewiz.prop.idlattributes
helpviewer_keywords:
- interfaces, adding properties
- properties [C++], adding to interfaces
- names, add property wizard
- IDL attributes, add property wizard
- stock properties, about stock properties
- stock properties
ms.assetid: 37bd4db7-efd3-4faa-87ad-64902ed16a36
ms.openlocfilehash: 125d7272b5b9fb0f656ba0621667885026e152fb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228670"
---
# <a name="add-a-property"></a>新增屬性

您可以使用 [[加入屬性] wizard](#names-add-property-wizard) ，將方法新增至專案中的介面。

**將屬性新增至物件：**

1. 在[類別檢視](/visualstudio/ide/viewing-the-structure-of-code)中，以滑鼠右鍵按一下您要新增屬性的介面名稱。

   > [!NOTE]
   > 您也可以將屬性新增至分配介面，除非專案有屬性，否則它會巢狀位於程式庫節點內。

1. 從捷徑功能表選擇 [新增]****，然後選擇 [新增屬性]****。

1. 在 [[加入屬性]](#names-add-property-wizard)中，提供用來建立屬性的資訊。

1. 在 wizard 的 [ [IDL 屬性](#idl-attributes-add-property-wizard)] 頁面中，指定屬性的任何介面定義語言（idl）設定。

1. 選取 [完成]**** 以新增屬性。

屬性的 `Get` 和 `Put` 方法會在 [類別檢視] 中定義它們的所在介面下顯示成兩個圖示。 您可以按兩下任一個圖示來檢視 .idl 檔案中的屬性宣告。

- 針對 ATL 介面，`Get` 和 `Put` 函式會新增至 .cpp 檔案中，而這些函式的參考會新增至 .h 檔案。

- 針對 MFC 分配介面，如果您選取 [成員變數]**** 作為實作類型，方法和變數會新增至實作它的類別。 如果您選取 [Get/Set 方法]**** 作為實作類型，兩種方法會新增至實作它的類別。

## <a name="in-this-section"></a>本節內容

- [名稱、新增屬性精靈](#names-add-property-wizard)
- [IDL 屬性、新增屬性精靈](#idl-attributes-add-property-wizard)
- [內建屬性](#stock-properties)

## <a name="names-add-property-wizard"></a>名稱、新增屬性精靈

使用此精靈將屬性新增至介面。

- **屬性類型**

  設定您要新增的屬性類型。 針對 MFC 分配介面 (Dispinterface)，提供您自己的類型，或從預先定義的清單中選取。 如果您提供屬性的內建實作，[屬性類型]**** 會設定為內建類型，而且無法變更。

- **屬性名稱**

  設定屬性的名稱。 針對與 ActiveX 控制項建立關聯的 MFC 分配介面 (Dispinterface)，您可以提供自己的名稱，或從預先定義的清單中選取內建屬性名稱。 如果您提供自己的屬性名稱，[內建]**** 實作類型無法使用。 如需清單中屬性的描述，請參閱[內建屬性](#stock-properties)。

  |介面類型|說明|
  |--------------------|-----------------|
  |ATL 雙重介面、自訂介面和本機自訂介面|提供屬性名稱。|
  |MFC 分配介面 (Dispinterface)、MFC ActiveX 控制項分配介面 (Dispinterface)|提供屬性名稱，或從清單中選取內建屬性。 如果您從清單中選取屬性，[屬性類型]**** 方塊中會顯示適當的值。 根據您在 [實作類型]**** 下的選擇，您可以變更此類型。|

- **傳回類型**

  僅限 ATL 介面。 設定屬性的傳回型別。 若是雙重介面，傳回型別一律是 `HRESULT`，而且此方塊無法使用。 若是自訂介面，您可以從清單中選取傳回型別。 仍建議使用 `HRESULT`，因為它提供傳回錯誤的標準方式。

- **變數名稱**

  僅限 MFC 分配介面 (Dispinterface)。 只有在 [實作類型]**** 下指定 [成員變數]**** 時，才可以使用。 設定與屬性建立關聯之成員變數的名稱。 根據預設，變數名稱會設定為 `m_`*PropertyName*。 您可以編輯此名稱。

- **通知函式**

  僅限 MFC 分配介面 (Dispinterface)。 只有在 [實作類型]**** 下指定 [成員變數]**** 時，才可以使用。 設定屬性變更時所呼叫之通知函式的名稱。 根據預設，通知函式的名稱會設定為 `On` *PropertyName* `Changed` 。 您可以編輯此名稱。

- **Get 函式**

  適用於 MFC 分配介面 (Dispinterface)。 只有在 [實作類型]**** 下指定 [Get/Set 方法]**** 時，才可以使用。 設定要取得屬性之函式的名稱。 根據預設，`Get` 函式的名稱會設定為 `Get`*PropertyName*。 您可以編輯此名稱。 如果您刪除名稱，則會將函式 [GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported) 插入介面分派對應。 `Get`*PropertyName* 函式指定屬性為可讀取。

- **Set 函式**

  僅限 MFC 分配介面 (Dispinterface)。 只有在 [實作類型]**** 下指定 [Get/Set 方法]**** 時，才可以使用。 設定要設定屬性之函式的名稱。 根據預設，`Set` 函式的名稱會設定為 `Set`*PropertyName*。 您可以編輯此名稱。 如果您刪除名稱，則會將函式 [SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported) 插入介面分派對應。 `Set`*PropertyName* 函式指定屬性為可寫入。

- **實作類型**

  僅限 MFC 分配介面 (Dispinterface)。 指定如何實作您要新增的屬性。

  |實作類型|說明|
  |-------------------------|-----------------|
  |**內建**|為 [屬性名稱]**** 中選取的屬性指定內建實作。 預設值。 如需詳細資訊，請參閱[內建屬性](#stock-properties)。<br /><br /> 如果您指定 [內建]****，則 [屬性類型]****、[參數類型]**** 和 [參數名稱]**** 都會呈暗灰色。|
  |**成員變數**|指定屬性已新增為成員變數。 您可以新增自訂屬性或大多數內建屬性作為成員變數。 您不能指定、和屬性的**成員變數** `Caption` `hWnd` `Text` 。<br /><br /> 在 [變數名稱]**** 和 [通知函式]**** 下提供預設名稱。 您可以編輯此名稱。|
  |**Get/Set 方法**|指定屬性根據預設新增為 `Get`*PropertyName* 及 `Set`*PropertyName* 函式。 這些名稱會出現在 [Get 函式]**** 和 [Set 函式]**** 下。<br /><br /> 您可以變更預設的 [屬性類型]****，這會傳遞 Get 函式的值。 您可以為 `Get` 及 `Set` 函式指定參數。|

- **Get 函式**

  適用於 ATL 介面。 將屬性設定為可讀取；也就是說，該屬性會建立 `Get` 方法，以從物件擷取此屬性。 選取 [Get]****、[Put]****，或兩者。

- **Put 函式**

  僅限 ATL 介面。 將屬性設定為可寫入；也就是說，它會建立 `Put` 方法，以設定或「放置」物件的這個屬性。 選取 [Get]****、[Put]****，或兩者。 如果您選取此選項，您可以選擇下列兩個方式來實作方法：

  |選項|說明|
  |------------|-----------------|
  |**PropPut**|[PropPut](../windows/propput.md) 函式會傳回物件的複本。 這是預設值，而且是將屬性設為可寫入的最常見方式。|
  |**PropPutRef**|[PropPutRef](../windows/propputref.md) 函式會傳回物件的參考，而不是傳回物件本身的複本。 請考慮針對大型結構或陣列等物件使用此選項，這類物件可能會有初始設定額外負荷。|

- **參數屬性**

  僅限 ATL 介面。 設定**參數名稱**所指定的參數是 `in` 、 `out` 、兩者或無。

  |選項|說明|
  |------------|-----------------|
  |`in`|表示參數會從呼叫程序傳遞至被呼叫程序。|
  |`out`|表示指標參數會從被呼叫程序傳回至呼叫程序 (從伺服器至用戶端)。|

- **參數類型**

  設定參數的資料類型。 請從清單中選取類型。

- **參數名稱**

  若屬性具有參數，請設定您要為屬性新增的參數名稱。 選取 [新增]**** 後，參數名稱會出現在 [參數清單]**** 中。

- **參數清單**

  顯示要新增至屬性 (Property) 的屬性 (Attribute) 清單。 清單中的每個項目是由參數名稱、參數類型和屬性所組成。 使用 [新增]**** 和 [移除]**** 更新清單。

- **加入**

  將您在 [參數名稱]**** 和 [參數類型]**** 中指定的參數新增至 [參數清單]****。 選取 [新增]**** 即可將參數新增至清單。

- **移除**

  移除您在 [參數清單]**** 中選取的參數。

- **預設屬性**

  僅限 MFC 分配介面 (Dispinterface)。 將此屬性設定為介面的預設值。 一個介面只能有一個預設屬性；指定預設屬性之後，對於您新增至介面的任何其他屬性，此方塊無法使用。

## <a name="idl-attributes-add-property-wizard"></a>IDL 屬性、新增屬性精靈

[新增屬性精靈] 的這個頁面可用來指定屬性的任何介面定義語言 (IDL) 設定。

- `id`

  設定識別屬性的數值識別碼。 此選項不適用於自訂介面的屬性。 請參閱＜MIDL 參考＞** 中的 [id](/windows/win32/Midl/id)。

- `helpcontext`

  指定內容識別碼，讓使用者可在說明檔中檢視此屬性的相關資訊。 請參閱＜MIDL 參考＞** 中的 [helpcontext](/windows/win32/Midl/helpcontext)。

- `helpstring`

  指定用來描述所套用元素的字元字串。 根據預設，它會設定為 [ **`property`** &nbsp; *屬性 &nbsp; 名稱*]。 請參閱＜MIDL 參考＞** 中的 [helpstring](/windows/win32/Midl/helpstring)。

### <a name="other-options"></a>其他選項

並非所有選項都適用於所有屬性類型。

|選項|說明|
|------------|-----------------|
|`bindable`|表示支援資料繫結的屬性。 請參閱＜MIDL 參考＞** 中的 [bindable](/windows/win32/Midl/bindable)。 對於屬性的內建實作，預設會設定此選項，而且無法變更。|
|`defaultbind`|表示這個單一可繫結屬性最能代表物件。 請參閱＜MIDL 參考＞** 中的 [defaultbind](/windows/win32/Midl/defaultbind)。|
|`displaybind`|表示這個屬性應向使用者顯示為可繫結。 請參閱＜MIDL 參考＞** 中的 [displaybind](/windows/win32/Midl/displaybind)。|
|`immediatebind`|表示該資料庫將立即被告知此資料繫結物件屬性的所有變更。 請參閱＜MIDL 參考＞** 中的 [immediatebind](/windows/win32/Midl/immediatebind)。|
|`defaultcollelem`|表示屬性是預設集合項目的存取子函式。 請參閱＜MIDL 參考＞** 中的 [defaultcollelem](/windows/win32/Midl/defaultcollelem)。|
|`nonbrowsable`|標記不應顯示在屬性瀏覽器中的介面或分派介面成員。 請參閱＜MIDL 參考＞** 中的 [nonbrowsable](/windows/win32/Midl/nonbrowsable)。|
|`requestedit`|表示屬性支援 `OnRequestEdit` 通知。 請參閱＜MIDL 參考＞** 中的 [requestedit](/windows/win32/Midl/requestedit)。 對於屬性的內建實作，預設會設定此選項，而且無法變更。|
|`source`|表示屬性的成員是事件來源。 請參閱＜MIDL 參考＞** 中的 [source](/windows/win32/Midl/source)。|
|`hidden`|表示屬性存在，但不應該在使用者導向的瀏覽器中顯示。 請參閱＜MIDL 參考＞** 中的 [hidden](/windows/win32/Midl/hidden)。|
|`restricted`|指定無法任意呼叫屬性。 請參閱＜MIDL 參考＞** 中的 [restricted](/windows/win32/Midl/restricted)。|
|`local`|對 MIDL 編譯器指定屬性不是遠端。 請參閱＜MIDL 參考＞** 中的 [local](/windows/win32/Midl/local)。|

## <a name="stock-properties"></a>內建屬性

若要使用 [[新增屬性精靈]](#idl-attributes-add-property-wizard) 將屬性新增至 MFC 分派介面，您可以在精靈的 [[名稱]](../ide/names-add-property-wizard.md) 頁面中，從 [屬性名稱]**** 清單選擇內建屬性。 這些屬性如下所示：

|屬性名稱|描述|
|-------------------|-----------------|
|`Appearance`|傳回或設定值，這個值可決定控制項的外觀。 控制項的 `Appearance` 屬性可以包含或省略立體顯示效果。 此屬性為環境讀取/寫入屬性。|
|`BackColor`|傳回控制項的環境 `BackColor` 屬性，或設定為調色盤 (RGB) 色彩或預先定義的系統色彩。 根據預設，其值會對應至控制項容器的前景色彩。 此屬性為環境讀取/寫入屬性。|
|`BorderStyle`|傳回或設定控制項的框線樣式。 此屬性為讀取/寫入屬性。|
|`Caption`|傳回或設定控制項的 `Caption` 屬性。 Caption 是視窗的標題。 `Caption` 沒有 [成員變數]**** 實作類型。|
|`Enabled`|傳回或設定控制項的 `Enabled` 屬性。 啟用的控制項可以回應使用者產生的事件。|
|`Font`|傳回或設定控制項的環境字型。 如果控制項沒有字型，則為 Null。|
|`ForeColor`|傳回或設定控制項的環境 `ForeColor` 屬性。|
|`hWnd`|傳回或設定控制項的 `hWnd` 屬性。 `hWnd` 沒有 [成員變數]**** 實作類型。|
|`ReadyState`|傳回或設定控制項的 `ReadyState` 屬性。 控制項可以是未初始化、已初始化、正在載入、互動式或完成。 如需詳細資訊，請參閱*網際網路 SDK* 中的 [READYSTATE](/previous-versions/aa768362\(v=vs.85\))。|
|`Text`|傳回或設定控制項內含的文字。 `Text` 沒有 [成員變數]**** 實作類型。|
