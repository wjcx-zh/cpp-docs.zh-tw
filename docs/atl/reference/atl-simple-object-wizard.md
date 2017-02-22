---
title: "ATL 簡單物件精靈 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.class.atl.simple.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 專案, 加入物件"
  - "ATL 簡單物件精靈"
ms.assetid: f7f85741-9aad-4543-a917-a29b996364da
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# ATL 簡單物件精靈
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個精靈可將最小的 COM 物件插入至專案。  使用這個精靈頁面來為物件及其 COM 功能指定識別 C\+\+ 類別 \(Class\) 和檔案的名稱。  
  
 您可以使用這個精靈的[選項](../../atl/reference/options-atl-simple-object-wizard.md)頁面，指定物件的執行緒模型、彙總支援以及是否要支援雙重介面和 Automation。  也可以指定錯誤資訊介面、連接點 \(Connection Point\)、Internet Explorer 支援及無限制執行緒封送處理 \(Marshaling\) 的支援。  
  
## 備註  
 從 [!INCLUDE[vs_orcas_long](../../atl/reference/includes/vs_orcas_long_md.md)] 開始，此精靈產生的註冊指令碼將會在 **HKEY\_CURRENT\_USER** 下 \(而非 **HKEY\_LOCAL\_MACHINE** 下\) 註冊它的 COM 元件。  若要修改此行為，請設定 \[ATL 精靈\] 的 \[**登錄所有使用者的元件**\] 選項。  
  
## 名稱  
 指定要加入專案的物件、介面和類別 \(Class\) 名稱。  除了 \[**簡短名稱**\] 之外，其他方塊都可以單獨進行編輯。  如果您變更 \[簡短名稱\] 當中的文字，這個頁面中所有其他方塊的名稱都將反映此變更。  如果您變更 \[COM\] 區段中的 \[Coclass\] 名稱，這項變更會反映在 \[型別\] 和 \[ProgID\] 方塊中，但是 \[介面\] 名稱則不受影響。  這項命名行為可讓您在開發控制項時能更容易識別所有的名稱。  
  
> [!NOTE]
>  **Coclass** 只能在未使用屬性的專案上進行編輯。  如果您的專案已經屬性化，您便無法編輯 **Coclass**。  
  
## C\+\+  
 提供為物件建立的 C\+\+ 類別相關資訊。  
  
 **簡短名稱**  
 設定物件的縮寫名稱。  除非針對個別欄位進行變更，否則您提供的名稱將決定 \[`Class`\] 和 \[**Coclass**\] 名稱、\[**.cpp 檔案**\] 和 \[**.h 檔案**\] 名稱、\[**介面**\] 名稱、\[**型別**\] 名稱以及 \[**ProgID**\]。  
  
 **.h 檔案**  
 為新物件類別設定標頭檔 \(Header File\) 的名稱。  根據預設，這個名稱是根據您在 \[**簡短名稱**\] 中提供的名稱來命名。  按一下省略按鈕，將檔名儲存至您選擇的位置，或將類別宣告附加至現有的檔案。  如果您選擇現有檔案，則要按一下精靈中的 \[**完成**\] 將檔名儲存至選取的位置。  
  
 精靈不會覆寫檔案。  如果您選取現有檔案的名稱，則當您按一下 \[**完成**\] 時，精靈會提示您是否要將類別宣告附加至檔案內容。  按一下 \[**是**\] 會將類別宣告附加至檔案，按一下 \[**否**\] 則可回到精靈並指定另一個檔名。  
  
 **類別**  
 設定要建立類別的名稱。  這個名稱會根據您在 \[**簡短名稱**\] 中提供的名稱來命名，並在前端加上類別名稱慣用的前置字元 'C'。  
  
 **.cpp 檔**  
 為新物件類別設定實作檔 \(Implementation File\) 的名稱。  根據預設，這個名稱是根據您在 \[**簡短名稱**\] 中提供的名稱來命名。  按一下省略按鈕，將檔名儲存至您選擇的位置。  除非您在精靈中按一下 \[**完成**\]，否則精靈不會將檔案儲存至選取的位置。  
  
 精靈不會覆寫檔案。  如果您選取現有檔案的名稱，則當您按一下 \[**完成**\] 時，精靈會提示您是否要將類別實作 附加至檔案內容。  按一下 \[**是**\] 會將類別宣告附加至檔案，按一下 \[**否**\] 則可回到精靈並指定另一個檔名。  
  
 **屬性化**  
 表示物件是否使用屬性 \(Attribute\)。  如果您正將物件加入至屬性化的 ATL 專案，則會選取這個選項，而且無法變更。  也就是說，您只能將屬性化物件加入至以屬性支援建立的專案。  
  
 您只能將屬性化物件加入至使用屬性的 ATL 專案。  如果您為沒有屬性支援的 ATL 專案選取這個選項，則精靈會提示您是否要在專案中加入屬性支援。  
  
 根據預設，您在設定此選項之後新增的所有物件都會指定為已設定屬性 \(已選取核取方塊\)。  您可以清除這個方塊以便加入不使用屬性的物件。  
  
 如需詳細資訊，請參閱 [ATL 專案精靈、應用程式設定](../../atl/reference/application-settings-atl-project-wizard.md)和[屬性的基本機制](../../windows/basic-mechanics-of-attributes.md)。  
  
## COM  
 提供物件的 COM 功能相關資訊。  
  
 **Coclass**  
 設定元件類別的名稱，這個類別包含物件所支援介面的清單。  
  
> [!NOTE]
>  如果您使用屬性建立專案，或是在這個精靈頁面上指示控制項要使用屬性，就無法變更這個選項，因為 ATL 不包含 `coclass` 屬性。  
  
 **Type**  
 設定將出現在登錄中的物件描述。  
  
 **介面**  
 設定為物件建立的介面。  這個介面包含自訂的方法。  
  
 **ProgID**  
 設定容器用來代替物件 CLSID 的名稱。  
  
## 請參閱  
 [ATL Simple Object](../../atl/reference/adding-an-atl-simple-object.md)