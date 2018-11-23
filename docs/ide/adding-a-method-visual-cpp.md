---
title: 新增方法
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.method.overview
- vc.codewiz.method.idlattrib
helpviewer_keywords:
- add method wizard [C++]
- methods [C++], adding
- methods [C++], adding using wizards
- IDL attributes, add method wizard
ms.assetid: 4ba4e45f-fa38-4d5e-af44-cbec0a7ab558
ms.openlocfilehash: 23fb05e633713016b1f6289f73a916502736af10
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "51692681"
---
# <a name="add-a-method"></a>新增方法

您可以使用[新增方法精靈](#add-method-wizard)，將方法新增至專案中的介面。 如果專案包含與介面建立關聯的類別，精靈也會修改類別。

**將方法新增至您的物件：**

1. 在 [類別檢視] 中，展開專案節點，以顯示您要新增方法的介面。

   > [!NOTE]
   > 您也可以將方法新增至分配介面，除非專案有屬性，否則它位於程式庫節點內。

1. 以滑鼠右鍵按一下介面的名稱。

1. 在捷徑功能表上選擇 [新增]，然後選擇 [新增方法]。

1. 在 [新增方法精靈] 中，提供建立方法用的資訊。

1. 在精靈的 [IDL 屬性](#idl-attributes-add-method-wizard)頁面，指定此方法的任何介面定義語言設定。

1. 按一下 [完成] 新增方法。

## <a name="in-this-section"></a>本節內容

- [新增方法精靈](#add-method-wizard)
- [新增方法精靈、IDL 屬性](#idl-attributes-add-method-wizard)

## <a name="add-method-wizard"></a>新增方法精靈

使用此精靈將方法新增至介面。 根據您要新增方法的專案類型或介面類型而定，精靈會顯示不同的選項。

### <a name="names"></a>名稱

- **傳回類型**

  方法傳回的資料類型。 建議針對所有介面類型使用 `HRESULT`，因為它提供傳回錯誤的標準方式。

  |介面類型|描述|
  |--------------------|-----------------|
  |雙重介面|`HRESULT`. 無法變更。|
  |自訂介面|`HRESULT`. 無法變更。|
  |本機自訂介面|提供您自己的傳回型別，或從清單中選取。|
  |分配介面 (Dispinterface)|提供您自己的傳回型別，或從清單中選取。|
  |MFC ActiveX 控制項分配介面|如果您實作內建方法，傳回型別則會設定為適當的值，而且無法變更。 如果您從 [方法名稱] 清單中選取方法，並選取 [選取方法類型] 下的 [自訂]，請從清單中選取傳回型別。|

- **方法名稱**

  設定方法的名稱。

  |介面類型|描述|
  |--------------------|-----------------|
  |ATL 雙重介面、自訂介面和本機自訂介面|提供您自己的方法名稱。|
  |MFC 分配介面|提供您自己的方法名稱，或從清單中選取建議的方法名稱。 如果您從清單中選取名稱，適當的值會出現在 [傳回型別] 方塊中，而且該值無法變更。|
  |MFC ActiveX 控制項分配介面|提供您自己的內建方法，或選取其中一個內建方法 ([DoClick](../mfc/reference/colecontrol-class.md#doclick) 和 [Refresh](../mfc/reference/colecontrol-class.md#refresh))。 如需詳細資訊，請參閱 [MFC ActiveX 控制項：新增內建方法](../mfc/mfc-activex-controls-adding-stock-methods.md)。|

- **方法類型**

  僅適用於 MFC ActiveX 控制項。 如果您在 [方法名稱] 方塊中提供方法名稱，而不是從清單中選取一種方法，就無法使用此方塊。

  如果您在 [方法名稱] 清單中選取其中一個方法，請選取內建實作或自訂實作。

  |方法類型|描述|
  |-----------------|-----------------|
  |**內建**|預設值。 插入您在 [方法名稱] 清單中所選取之方法的內建實作。 如果您選取 [內建] 則無法變更 [傳回型別]。|
  |**自訂**|插入您在 [方法名稱] 清單中所選取之方法的虛設常式實作。 若為自訂方法類型，您可以提供您自己的傳回型別，也可以從 [傳回型別] 清單中選取傳回型別。|

- **內部名稱**

  僅適用於新增至 MFC 分配介面的自訂方法。 請設定用於分派對應、 標頭檔 (.h) 和實作檔 (.cpp) 的名稱。 根據預設，此名稱與 [方法名稱] 相同。 如果您要使用 MFC 分配介面，或者要將自訂方法新增至 MFC ActiveX 控制項分配介面中，則可以變更方法名稱。

  |介面類型|描述|
  |--------------------|-----------------|
  |ATL 雙重介面、自訂介面和本機自訂介面|不適用。|
  |MFC 分配介面|預設設定為方法名稱。 您可以編輯內部名稱。|
  |MFC ActiveX 控制項分配介面|您只能為自訂方法設定內部名稱。 內建方法不會使用內部名稱。|

- **參數屬性**

  為 [參數名稱] 中指定的參數設定任何其他屬性。

  |參數屬性|描述|允許的組合|
  |-------------------------|-----------------|--------------------------|
  |**In**|表示參數會從呼叫程序傳遞至被呼叫程序。|僅限 `in`<br /><br /> `in` 和 `out`|
  |**Out**|表示指標參數會從被呼叫程序傳回至呼叫程序 (從伺服器至用戶端)。|僅限 `out`<br /><br /> `in` 和 `out`<br /><br /> `out` 和 `retval`|
  |**Retval**|表示接收成員傳回值的參數。|`retval` 和 `out`|

- **參數型別**

  設定參數的資料類型。 請從清單中選取類型。

- **參數名稱**

  設定要透過方法傳遞的參數名稱。 鍵入名稱之後，請選取 [新增]，將它新增至將透過方法傳遞的參數清單。 如果您未提供參數名稱，則精靈會忽略任何參數屬性 (僅限於 ATL) 或 [參數類型] 選取項目。

  選取 [新增] 後，參數名稱會出現在 [參數清單] 中。

  > [!NOTE]
  > 如果您提供參數名稱，然後選取 [完成] 再選取 [新增]，則參數不會新增至方法。 您必須尋找方法，並手動插入參數。

- **[新增]**

  將您在 [參數名稱] 中指定的參數以及其類型和參數屬性，新增至 [參數清單]。 選取 [新增]，將參數新增至清單中。

- **移除**

  將您在 [參數清單] 中選取的參數從清單移除。

- **參數清單**

  顯示目前針對方法新增的所有參數及其修飾詞和類型。 新增參數時，精靈會更新 [參數清單] 以顯示每個參數及其修飾詞和類型。

## <a name="idl-attributes-add-method-wizard"></a>新增方法精靈、IDL 屬性

[新增方法精靈] 的這個頁面可用來指定方法的任何介面定義語言 (IDL) 設定。

- `id`

  設定識別方法的數值識別碼。 如需詳細資訊，請參閱＜MIDL 參考＞中的 [id](/windows/desktop/Midl/id)。

  此方塊不適用於自訂介面，也不適用於 MFC 分配介面。

- `call_as`

  指定此區域方法可對應之遠端方法的名稱。 如需詳細資訊，請參閱＜MIDL 參考＞中的 [call_as](/windows/desktop/Midl/call-as)。

  不適用於 MFC 分配介面 (Dispinterface)。

- `helpcontext`

  指定內容識別碼，讓使用者可在說明檔中檢視此方法的相關資訊。 如需詳細資訊，請參閱＜MIDL 參考＞中的 [helpcontext](/windows/desktop/Midl/helpcontext)。

  不適用於 MFC 分配介面 (Dispinterface)。

- `helpstring`

  指定用來描述所套用項目的字元字串。 它預設會設定為 "method <方法名稱>"。 請參閱＜MIDL 參考＞中的 [helpstring](/windows/desktop/Midl/helpstring)。

  不適用於 MFC 分配介面 (Dispinterface)。

- **其他屬性**

  不適用於 MFC 分配介面 (Dispinterface)。

  |屬性|描述|
  |---------------|-----------------|
  |`hidden`|表示方法存在，但不應該在使用者導向的瀏覽器中顯示。 請參閱＜MIDL 參考＞中的 [hidden](/windows/desktop/Midl/hidden)。|
  |`source`|表示事件來源是方法的成員。 如需詳細資訊，請參閱＜MIDL 參考＞中的 [source](/windows/desktop/Midl/source)。|
  |`local`|對 MIDL 編譯器指定方法不是遠端。 如需詳細資訊，請參閱＜MIDL 參考＞中的 [local](/windows/desktop/Midl/local)。|
  |`restricted`|指定無法任意呼叫方法。 請參閱＜MIDL 參考＞中的 [restricted](/windows/desktop/Midl/restricted)。|
  |`vararg`|指定方法接受可變的引數數目。 若要完成這個工作，最後一個引數必須是包含其餘引數的 `VARIANT` 類型安全陣列。 如需詳細資訊，請參閱＜MIDL 參考＞中的 [vararg](/windows/desktop/Midl/vararg)。|
