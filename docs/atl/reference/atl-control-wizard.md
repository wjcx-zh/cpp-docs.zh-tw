---
title: "ATL 控制項精靈 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.class.atl.control.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 控制項精靈"
  - "ATL 專案, 加入控制項"
  - "[ATL] 的控制項, 加入至專案"
ms.assetid: 991f8e72-ffbc-4382-a4ce-e255acfba5b6
caps.latest.revision: 17
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL 控制項精靈
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將 ATL 控制項插入至 ATL 專案 \(或具有 ATL 支援的 MFC 專案\)。  您可使用這個精靈來插入以下任一類的控制項：  
  
-   標準控制項  
  
-   複合控制項  
  
-   DHTML 控制項  
  
 除此之外，您也可以指定一個最小控制項，從[介面](../../atl/reference/interfaces-atl-control-wizard.md)清單移除介面，介面是預設讓控制項可以在多數容器中開啟。  您可在精靈的 \[**介面**\] 頁面中設定控制項要支援的介面。  
  
## 備註  
 這個精靈所產生的註冊指令碼會將其 COM 元件登錄在 HKEY\_CURRENT\_USER 之下，而非 HKEY\_LOCAL\_MACHINE。  若要修改此行為，請設定 \[ATL 精靈\] 的 \[**登錄所有使用者的元件**\] 選項。  
  
## 名稱  
 指定要加入專案的物件、介面和類別 \(Class\) 名稱。  除了 \[**簡短名稱**\] 之外，其他方塊都可以單獨進行變更。  如果您變更 \[**簡短名稱**\] 的文字，這個頁面中所有其他方塊的名稱也都將反映此變更。  如果您變更 \[COM\] 區段中的 **\[Coclass\]** 名稱，這項變更會在 \[**型別**\] 方塊中反映，但 \[**介面**\] 名稱和 \[**ProgID**\] 則不會變更。  這項命名行為可讓您在開發控制項時能更容易識別所有的名稱。  
  
> [!NOTE]
>  **Coclass** 只能在未使用屬性的控制項上進行編輯。  如果您的專案已經屬性化，您便無法編輯 **Coclass**。  
  
### C\+\+  
 提供為實作物件而建立之 C\+\+ 類別的相關資訊。  
  
 **簡短名稱**  
 設定物件的縮寫名稱。  除非您針對個別欄位變更，否則您提供的名稱將決定類別和 \[**Coclass**\] 名稱、檔案 \(.CPP 和 .H\) 名稱、介面名稱，以及 \[**型別**\] 名稱。  
  
 **類別**  
 設定實作物件的類別名稱。  這個名稱會根據您在 \[**簡短名稱**\] 中提供的名稱來命名，並在前端加上類別名稱慣用的前置字元 'C'。  
  
 **.h 檔案**  
 為新物件類別設定標頭檔 \(Header File\) 的名稱。  根據預設，這個名稱是根據您在 \[**簡短名稱**\] 中提供的名稱來命名。  按一下省略按鈕，將檔名儲存至您選擇的位置，或將類別宣告附加至現有的檔案。  如果您選擇現有檔案，則要按一下 \[**完成**\] 將檔名儲存至選取的位置。  
  
 精靈不會覆寫檔案。  如果您選取現有檔案的名稱，則當您按一下 \[**完成**\] 時，精靈會提示您是否要將類別宣告附加至檔案內容。  按一下 \[**是**\] 會將類別宣告附加至檔案，按一下 \[**否**\] 則可回到精靈並指定另一個檔名。  
  
 **.cpp 檔**  
 為新物件類別設定實作檔 \(Implementation File\) 的名稱。  根據預設，這個名稱是根據您在 \[**簡短名稱**\] 中提供的名稱來命名。  按一下省略按鈕，將檔名儲存至您選擇的位置。  除非您在精靈中按一下 \[**完成**\]，否則精靈不會將檔案儲存至選取的位置。  
  
 精靈不會覆寫檔案。  如果您選取現有檔案的名稱，則當您按一下 \[**完成**\] 時，精靈會提示您是否要將類別實作 附加至檔案內容。  按一下 \[**是**\] 會將類別宣告附加至檔案，按一下 \[**否**\] 則可回到精靈並指定另一個檔名。  
  
 **屬性化**  
 表示物件是否使用屬性 \(Attribute\)。  如果您正將物件加入至屬性化的 ATL 專案，則會選取這個選項，而且無法變更。  也就是說，您只能將屬性化物件加入至以屬性支援建立的專案。  
  
 您只能將屬性化物件加入至使用屬性的 ATL 專案。  如果您為沒有屬性支援的 ATL 專案選取這個選項，則精靈會提示您是否要在專案中加入屬性支援。  
  
 根據預設，您在設定此選項之後新增的所有物件都會指定為已設定屬性 \(已選取核取方塊\)。  您可以清除這個方塊以便加入不使用屬性的物件。  
  
 如需詳細資訊，請參閱 [ATL 專案精靈、應用程式設定](../../atl/reference/application-settings-atl-project-wizard.md)和[屬性的基本機制](../../windows/basic-mechanics-of-attributes.md)。  
  
### COM  
 提供物件的 COM 功能相關資訊。  
  
 **Coclass**  
 設定元件類別的名稱，這個類別包含物件所支援介面的清單。  
  
> [!NOTE]
>  如果您使用屬性建立專案，或是在這個精靈頁面上指示控制項要使用屬性，就無法變更這個選項，因為 ATL 不包含 **coclass** 屬性。  
  
 **介面**  
 設定物件的介面名稱。  根據預設，介面名稱的開頭都會加上 "I"。  
  
 **Type**  
 設定將出現在登錄中的物件描述。  
  
 **ProgID**  
 設定容器用來代替物件 CLSID 的名稱。  這個欄位不會自動填入。  如果您不手動填入此欄位，其他工具可能無法使用該控制項。  例如，\[**插入 ActiveX 控制項**\] 對話方塊中不會有未使用  `ProgID` 而產生的 ActiveX 控制項。  如需這個對話方塊的詳細資訊，請參閱[插入 ActiveX 控制項對話方塊](../../mfc/insert-activex-control-dialog-box.md)。  
  
## 請參閱  
 [ATL Control](../../atl/reference/adding-an-atl-control.md)   
 [Adding Functionality to the Composite Control](../../atl/adding-functionality-to-the-composite-control.md)   
 [Fundamentals of ATL COM Objects](../../atl/fundamentals-of-atl-com-objects.md)