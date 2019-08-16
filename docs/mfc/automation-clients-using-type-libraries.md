---
title: 自動化用戶端:使用類型程式庫
ms.date: 11/04/2016
f1_keywords:
- MkTypLib
helpviewer_keywords:
- clients, Automation
- dispatch class [MFC]
- Automation clients, type libraries
- type libraries, Automation clients
- ODL (Object Description Language)
- ODL files
- classes [MFC], dispatch
- MkTypLib tool
- .odl files
ms.assetid: d405bc47-118d-4786-b371-920d035b2047
ms.openlocfilehash: 480f8fca46b13d445f372311ed837475c71a1e9d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509214"
---
# <a name="automation-clients-using-type-libraries"></a>自動化用戶端:使用類型程式庫

如果用戶端要操作伺服器物件, Automation 用戶端必須有伺服器物件的屬性和方法的相關資訊。 屬性的資料類型為;方法通常會傳回值並接受參數。 用戶端需要所有這些資料類型的相關資訊, 才能以靜態方式系結至伺服器物件類型。

這種類型的資訊可以透過數種方式來取得。 建議的方式是建立類型程式庫。

如需[mktyplib.exe](/windows/win32/Midl/differences-between-midl-and-mktyplib)的詳細資訊, 請參閱 Windows SDK。

視覺C++效果可以讀取型別程式庫檔案, 並建立衍生自[COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)的分派類別。 該類別的物件具有複製伺服器物件的屬性和作業。 您的應用程式會呼叫這個物件的屬性和作業, 而`COleDispatchDriver`繼承自的功能會將這些呼叫路由傳送至 OLE 系統, 然後再將它們路由傳送至伺服器物件。

如果C++您選擇在建立專案時加入自動化, 視覺效果會自動為您維護此型別程式庫檔案。 在每個組建中, 會以 Mktyplib.exe 建立 .tlb 檔案。

### <a name="to-create-a-dispatch-class-from-a-type-library-tlb-file"></a>從類型程式庫 (.tlb) 檔案建立分派類別

1. 在類別檢視或方案總管中, 以滑鼠右鍵按一下專案, 然後按一下 [**加入**], 再按一下快捷方式功能表上的 [**加入類別**]。

1. 在 [**加入類別**] 對話方塊中, 選取左窗格中的 [ **Visual C++/MFC** ] 資料夾。 從右窗格中選取 [**來自 TypeLib 的 MFC 類別**] 圖示, 然後按一下 [**開啟**]。

1. 在 [**從 Typelib 新增類別]** 對話方塊中, 從 [**可用的型別程式庫**] 下拉式清單中選取類型程式庫。 [**介面**] 方塊會顯示所選類型程式庫可用的介面。

    > [!NOTE]
    >  您可以從一個以上的類型程式庫選取介面。

   若要選取介面, 請按兩下它們, 或按一下 [**加入**] 按鈕。 當您這麼做時, 分派類別的名稱會出現在 [**產生的類別**] 方塊中。 您可以編輯方塊中`Class`的類別名稱。

   [檔案] 方塊會顯示要在其中宣告類別的檔案。 (您也可以編輯此檔案名)。 如果您想要將標頭和執行資訊寫入現有檔案或專案目錄以外的目錄中, 也可以使用 [流覽] 按鈕來選取其他檔案。

    > [!NOTE]
    >  所選取介面的所有分派類別都會放入此處指定的檔案中。 如果您想要在個別的標頭中宣告介面, 您必須針對每個要建立的標頭檔執行此 wizard。

    > [!NOTE]
    >  某些類型的程式庫資訊可能會以儲存在檔案中。DLL、.OCX 或.OLB 副檔名。

1. 按一下 [ **完成**]。

   接著, 此 wizard 會使用指定的類別和檔案名, 為您的分派類別撰寫程式碼。

## <a name="see-also"></a>另請參閱

[Automation 用戶端](../mfc/automation-clients.md)
