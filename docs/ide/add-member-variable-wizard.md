---
title: "加入成員變數精靈 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.variable.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "加入成員變數精靈 [C++]"
ms.assetid: 73e8fa99-ac1a-42e2-8fc2-4684b9eb6d4d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 加入成員變數精靈
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個精靈會在標頭檔 \(Header File\) 中加入成員變數宣告，並且根據選項，將程式碼加入 .cpp 檔中。  使用精靈加入成員變數之後，您就能在開發環境中編輯程式碼。  
  
 **存取權**  
 設定對成員變數的存取。  存取修飾詞 \(Modifier\) 是指定其他類別對成員變數之存取的關鍵字。  如需關於指定存取的詳細資訊，請參閱[成員存取控制](../cpp/member-access-control-cpp.md) \(Member\-Access Control\)。  預設的成員變數存取等級為 **public**。  
  
-   [public](../cpp/public-cpp.md)  
  
-   [protected](../cpp/protected-cpp.md)  
  
-   [private](../cpp/private-cpp.md)  
  
 **變數型別**  
 設定您加入之成員變數的傳回型別。  
  
-   如果加入的成員變數不是一個對話方塊控制項，請從可用型別清單中選取。  
  
     如需有關型別的資訊，請參閱[主要資料型別](../cpp/fundamental-types-cpp.md) \(Fundamental Type\)。  
  
    |||  
    |-|-|  
    |`char`|**short**|  
    |**double**|`unsigned char`|  
    |**float**|`unsigned int`|  
    |`int`|`unsigned long`|  
    |**long**||  
  
-   如果是為對話方塊控制項加入成員變數，這個方塊將填入傳回作控制項或數值的物件型別。  若您選取了 \[控制項\] 選項，則 \[變數型別\] 指定的是在 \[控制項 ID\] 方塊中選取之控制項的基底類別 \(Base Class\)。  若對話方塊控制項可以包含數值，且您選取了 \[**值**\]，則 \[變數型別\] 會指定控制項所能包含之數值的適當型別。  如需詳細資訊，請參閱[對話方塊控制項和變數型別](../ide/dialog-box-controls-and-variable-types.md)。  
  
     本數值依據 \[控制項 ID\] 內的選取而定，且無法變更。  
  
 **變數名稱**  
 設定加入之成員變數的名稱。  成員變數通常以預設的識別字串「m\_」起頭。  
  
 **控制項變數**  
 指出成員變數使用[資料交換和資料驗證](../mfc/dialog-data-exchange-and-validation.md)支援，管理對話方塊內的控制項。  如需詳細資訊，請參閱 [DoDataExchange](../Topic/CWnd::DoDataExchange.md)。  本選項僅適用在加到衍生於 [CDialog](../mfc/reference/cdialog-class.md) 類別的成員變數。  選取本對話方塊可啟動 \[控制項 ID\] 和 \[控制項型別\] 二選項。  
  
 **控制項 ID**  
 設定您加入之控制項變數的 ID。  自清單中選取您所加入成員變數控制項的 ID 型別。  唯有當選取了 \[控制項變數\] 方塊，該清單方為作用中，且僅限已經加入對話方塊的控制項 ID。  例如，對標準的 \[**確定**\] 按鈕而言，其控制項 ID 為 \[IDOK\]。  
  
|選項|描述|  
|--------|--------|  
|**控制項**|本選項為預設設定的控制項型別。  所管理的是控制項本身，而非控制項的狀態或內容 \(如一般對清單方塊、下拉式方塊或編輯方塊的作法\)。|  
|**值**|本選項僅供可包含值的控制項型別 \(如編輯方塊\) 或反映狀態 \(如核取方塊\)，及可能用來管理範圍、內容或狀態的型別。  如需詳細資訊，請參閱[對話方塊控制項和變數型別](../ide/dialog-box-controls-and-variable-types.md)。|  
  
 **分類**  
 指定變數是根據控制項型別或控制項的值。  
  
 **控制項型別**  
 設定加入的控制項型別。  本方塊無法變更。  例如，按鈕的控制項型別為 **BUTTON**，而下拉式方塊的控制項型別為 **COMBOBOX**。  如需詳細資訊，請參閱[對話方塊控制項和變數型別](../ide/dialog-box-controls-and-variable-types.md)。  
  
 **最大字元數**  
 只有當變數型別設成 [CString](../atl-mfc-shared/reference/cstringt-class.md) 時才可用。  表示控制項所能儲存的最大字元數。  
  
 **最小值**  
 唯有當變數型別是 **BOOL**、`int`、**UINT**、**long**、`DWORD`、**float**、**double**、**BYTE**、**short**、[COLECurrency](../mfc/reference/colecurrency-class.md) 或 [CTime](../atl-mfc-shared/reference/ctime-class.md) 時可用。  表示小數位數或日期範圍可接受的最小數值。  
  
 **最大值**  
 唯有當變數型別是 **BOOL**、`int`、**UINT**、**long**、`DWORD`、**float**、**double**、**BYTE**、**short**、`COLECurrency` 或 `CTime` 時可用。  表示小數位數或日期範圍可接受的最大數值。  
  
 **.h 檔案**  
 供需要包裝函式類別做為成員變數的 ActiveX 控制項使用。  設定標頭檔的名稱以加入類別宣告 \(Class Declaration\)。  
  
 **.cpp 檔**  
 供需要包裝函式類別做為成員變數的 ActiveX 控制項使用。  設定實作檔 \(Implementation File\) 的名稱以加入類別定義。  
  
 **註解**  
 在標頭檔中提供成員變數的註解。  
  
## 請參閱  
 [加入成員變數](../ide/adding-a-member-variable-visual-cpp.md)