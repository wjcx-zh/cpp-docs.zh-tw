---
title: Automation 用戶端： 使用型別程式庫 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- MkTypLib
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 421040024e5dd95fb39bdc78cd54f3f7dc49bf83
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377706"
---
# <a name="automation-clients-using-type-libraries"></a>Automation 用戶端：使用類型程式庫

Automation 用戶端必須具有伺服器物件的屬性和方法的相關資訊，如果用戶端管理的伺服器物件。 屬性有資料類型;方法通常會傳回值，而且接受參數。 用戶端需要的所有這些資料類型的相關資訊，才能以靜態方式繫結至該伺服器物件類型。

此類型資訊可以成為已知數種方式。 建議的方式是建立型別程式庫。

如需[MkTypLib](/windows/desktop/Midl/differences-between-midl-and-mktyplib)，請參閱 Windows SDK。

Visual c + + 可以讀取類型程式庫檔案，並建立分派類別衍生自[COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)。 該類別的物件具有屬性和複製的伺服器物件的作業。 這個物件的屬性和作業，會呼叫您的應用程式和功能會繼承自`COleDispatchDriver`這些將來電路由到 OLE 系統接著會路由傳送到伺服器物件。

如果您選擇要建立專案時，包含自動化 visual c + + 會自動為您維護此型別程式庫檔案。 隨著每個組建的詳細資訊，將會建置 MkTypLib.tlb 檔案。

### <a name="to-create-a-dispatch-class-from-a-type-library-tlb-file"></a>若要從型別程式庫 (.tlb) 檔案建立分派類別

1. 在 類別檢視或方案總管 中，以滑鼠右鍵按一下專案，然後按一下 **新增**，然後按一下**加入類別**快顯功能表。

1. 在 **加入類別**對話方塊中，選取**Visual c + + MFC**的左窗格中的資料夾。 選取 **從 TypeLib 的 MFC 類別**圖示從右窗格，然後按一下**開啟**。

1. 在 **加入類別從 Typelib 精靈**對話方塊方塊中，選取從類型程式庫**可用的型別程式庫**下拉式清單。 **介面**方塊會顯示所選的型別程式庫的介面。

    > [!NOTE]
    >  您可以從一個以上的類型程式庫選取介面。

     若要選擇的介面，按兩下或按一下 [**新增**] 按鈕。 當您這樣做的時候時，分派類別名稱會出現在**產生的類別** 方塊中。 您可以編輯中的類別名稱`Class` 方塊中。

     **檔案**方塊會顯示此類別會宣告的檔案。 （您可以編輯此檔案名稱）。 您也可以使用瀏覽按鈕來選取其他檔案中，如果您想要有寫入在現有的檔案或專案目錄以外的目錄中的標頭和實作資訊。

    > [!NOTE]
    >  所選介面的所有分派類別便會都放在這裡指定的檔案。 如果您想要在個別的標頭中宣告的介面，您必須執行此精靈為您想要建立每個標頭檔案。

    > [!NOTE]
    >  某些類型程式庫的資訊可能儲存在檔案中。DLL。OCX，或。OLB 檔案副檔名。

1. 按一下 [ **完成**]。

     精靈接著會寫入分派類別使用指定的類別和檔案名稱的程式碼。

## <a name="see-also"></a>另請參閱

[Automation 用戶端](../mfc/automation-clients.md)

