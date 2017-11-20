---
title: "Automation 用戶端： 使用類型程式庫 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MkTypLib
dev_langs: C++
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
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 696765451079301e2a25cc831c34e41802dd33f9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="automation-clients-using-type-libraries"></a>Automation 用戶端：使用類型程式庫
Automation 用戶端必須具有伺服器物件的屬性和方法的相關資訊，如果用戶端管理伺服器的物件。 屬性有資料類型。方法通常會傳回值，而且接受參數。 用戶端需要所有這些資料類型的相關資訊，才能以靜態方式將繫結至該伺服器物件類型。  
  
 此類型資訊可以做為已知數種方式。 建議的方式是建立類型程式庫。  
  
 如需有關詳細[MkTypLib](http://msdn.microsoft.com/library/windows/desktop/aa366797)，請參閱 Windows SDK。  
  
 Visual c + + 可以讀取類型程式庫檔案並建立分派類別衍生自[COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)。 該類別的物件具有屬性和伺服器物件的複製作業。 此物件的屬性和作業，會呼叫您的應用程式和功能繼承自`COleDispatchDriver`OLE 系統接著會路由傳送到伺服器物件的呼叫會路由傳送。  
  
 如果您選擇要建立專案時，包含自動化 visual c + + 會自動為您維護此型別程式庫檔案。 每個組建的一部分，會使用 MkTypLib 建置.tlb 檔案。  
  
### <a name="to-create-a-dispatch-class-from-a-type-library-tlb-file"></a>若要從類型程式庫 (.tlb) 檔案建立分派類別  
  
1.  在 類別檢視或方案總管 中，以滑鼠右鍵按一下專案，然後按一下**新增**，然後按一下 **加入類別**快顯功能表。  
  
2.  在**加入類別**對話方塊中，選取**Visual C + MFC**的左窗格中的資料夾。 選取**從 TypeLib 的 MFC 類別**圖示從右窗格，然後按一下**開啟**。  
  
3.  在**加入類別從 Typelib 精靈**對話方塊方塊中，選取從類型程式庫**可用的型別程式庫**下拉式清單。 **介面**方塊會顯示選取的類型程式庫的介面。  
  
    > [!NOTE]
    >  您可以從一個以上的類型程式庫中選取的介面。  
  
     若要選擇的介面，連按兩下，或按一下**新增** 按鈕。 當您這樣做時，分派類別名稱會出現在**產生的類別**方塊。 您可以編輯中的類別名稱`Class`方塊。  
  
     **檔案**方塊會顯示此類別會宣告的檔案。 （您可以編輯此檔案名稱）。 您也可以使用瀏覽按鈕來選取其他檔案中，如果您想要有寫入現有的檔案或專案目錄以外的目錄中的標頭和實作資訊。  
  
    > [!NOTE]
    >  所選介面的所有分派類別將會都進入此指定的檔案。 如果您想要在個別的標頭中宣告的介面，您必須執行此精靈，您想要建立每個標頭檔。  
  
    > [!NOTE]
    >  某些類型程式庫的資訊可能會儲存在檔案中。DLL。OCX，或。OLB 副檔名。  
  
4.  按一下 [ **完成**]。  
  
     精靈接著將要撰寫的程式碼，為您的分派類別，使用指定的類別和檔案名稱。  
  
## <a name="see-also"></a>另請參閱  
 [Automation 用戶端](../mfc/automation-clients.md)

