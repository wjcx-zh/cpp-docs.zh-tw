---
title: 加入控制項 (ATL 教學課程，第 2 部分) |Microsoft 文件
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c9575a75-1064-41f1-9697-7aada560c669
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d3b8c7eb59579363ce3580c7319b80be2557a30d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="adding-a-control-atl-tutorial-part-2"></a>加入控制項 (ATL 教學課程，第 2 部分)
在此步驟中，您將控制項加入您的專案，建置，和測試在網頁上。  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-add-an-object-to-an-atl-project"></a>將物件新增至 ATL 專案  
  
1.  在 類別檢視，以滑鼠右鍵按一下多邊形專案。  
  
2.  指向**新增**捷徑功能表，然後按一下 **新項目**子功能表中。  
  
     [新增項目] 對話方塊隨即出現。 在左側的樹狀結構中，會列出不同的物件類別。  
  
3.  按一下**ATL**資料夾。  
  
4.  從右側的範本清單中，選取**ATL 控制項**。 按一下 [加入] 。 ATL 控制項精靈隨即會開啟，並且可以設定控制項。  
  
5.  型別`PolyCtl`簡短名稱以及其他欄位會自動完成的附註。 不要在上面按一下**完成**尚未，因為您需要進行一些變更。  
  
 ATL 控制項精靈**名稱**頁面包含下列欄位：  
  
|欄位|內容|  
|-----------|--------------|  
|**簡短名稱**|您輸入控制項的名稱。|  
|**類別**|實作控制項建立的 c + + 類別名稱。|  
|**.h 檔案**|若要包含的 c + + 類別定義建立的檔案。|  
|**.cpp 檔案中**|若要包含的 c + + 類別實作所建立的檔案。|  
|**CoClass**|這個控制項的元件類別名稱。|  
|**Interface**|其自訂的方法和屬性，控制將實作的介面名稱。|  
|**Type**|控制項的描述。|  
|**ProgID**|可以用來查詢的 CLSID 控制項的可讀取的名稱。|  
  
 您必須在 ATL 控制項精靈中進行一些其他的設定。  
  
#### <a name="to-enable-support-for-rich-error-information-and-connection-points"></a>若要啟用支援豐富的錯誤資訊及連接點  
  
1.  按一下**選項**開啟**選項**頁面。  
  
2.  選取**連接點**核取方塊。 這會建立支援輸出介面 IDL 檔中。  
  
 您也可以將控制項可插入，這表示它可以內嵌入支援內嵌的物件，例如 Excel 或 Word 的應用程式。  
  
#### <a name="to-make-the-control-insertable"></a>將控制項設為可插入  
  
1.  按一下**外觀**開啟**外觀**頁面。  
  
2.  選取**Insertable**核取方塊。  
  
 物件所顯示多邊形就會有實心填滿色彩，所以您不必加入`Fill Color`內建屬性。  
  
#### <a name="to-add-a-fill-color-stock-property-and-create-the-control"></a>若要加入的填滿色彩的內建屬性，並建立控制項  
  
1.  按一下**內建屬性**開啟**內建屬性**頁面。  
  
2.  在下**不支援**，向下捲動清單的可能內建屬性。 按兩下`Fill Color`將其移至**支援**清單。  
  
3.  如此即完成控制項的選項。 按一下 [ **完成**]。  
  
 精靈建立控制項時，就發生數個程式碼變更和加入檔案。 已建立下列檔案：  
  
|檔案|描述|  
|----------|-----------------|  
|PolyCtl.h|包含大部分的 c + + 類別的實作`CPolyCtl`。|  
|PolyCtl.cpp|包含的其餘部分`CPolyCtl`。|  
|PolyCtl.rgs|包含用來登錄此控制項的登錄指令碼的文字檔。|  
|PolyCtl.htm|Web 網頁，其中包含新建立的控制項的參考。|  
  
 精靈也會執行下列程式碼變更：  
  
-   加入`#include`stdafx.h 和 stdafx.cpp 檔案，以包括 ATL 的陳述式的檔案所需的控制項。  
  
-   若要包含新控制項的詳細資料的變更的 Polygon.idl。  
  
-   物件中的對應 Polygon.cpp 加入新的控制項。  
  
 現在您可以建立要觀看它的運作的控制項。  
  
## <a name="building-and-testing-the-control"></a>建置和測試控制項  
  
#### <a name="to-build-and-test-the-control"></a>建置和測試控制項  
  
1.  在**建置**功能表上，按一下 **建置多邊形**。  
  
     當控制項完成建置時，以滑鼠右鍵按一下在 PolyCtl.htm**方案總管 中**選取**瀏覽器中的檢視**。 包含控制項的 HTML 網頁上隨即出現。 您應該會看到 「 ATL 物件 PolyCtl 8.0 測試頁 」 的標題和文字的頁面**PolyCtl**。 這是您的控制項。  
  
> [!NOTE]
>  當完成此教學課程中，如果您收到錯誤訊息，無法建立 DLL 檔案的位置後，關閉 PolyCtl.htm 檔案和 ActiveX 控制項測試容器，並再次建置方案。 如果您仍然無法建立 DLL，將電腦重新開機或登出 （如果您正在使用終端機服務）。  
  
 接下來，您會將自訂屬性加入控制項。  
  
 [步驟 1 至](../atl/creating-the-project-atl-tutorial-part-1.md) &#124; [至步驟 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md)  
  
## <a name="see-also"></a>另請參閱  
 [教學課程](../atl/active-template-library-atl-tutorial.md)

