---
title: "section | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "section_CPP"
  - "vc-pragma.section"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Pragma, section"
  - "section pragma"
ms.assetid: c67215e9-2c4a-4b0f-b691-2414d2e2d96f
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# section
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 .obj 檔案中建立區段。  
  
## 語法  
  
```  
  
#pragma section( "section-name" [, attributes] )  
```  
  
## 備註  
 在本主題中，「*區段*」\(Segment\) 和「*區段*」\(Section\) 這兩個詞的意義可互換。  
  
 區段定義之後，其仍適用於編譯的其餘部分。  不過，您必須使用 [\_\_declspec\(allocate\)](../cpp/allocate.md)，否則區段中不會有任何內容。  
  
 *section\-name* 是必要的參數，它將會是該區段的名稱。  名稱不得與任何標準區段名稱相衝突。  如需建立區段時不應該使用的名稱清單，請參閱 [\/SECTION](../build/reference/section-specify-section-attributes.md)。  
  
 `attributes` 是選擇性的參數，其中包含一個或多個逗號分隔的屬性，這些是您要指派給該區段的屬性。  可能的 `attributes` 為：  
  
 **read**  
 允許對於資料進行讀取作業。  
  
 **write**  
 允許對於資料進行寫入作業。  
  
 **execute**  
 允許執行程式碼。  
  
 **shared**  
 讓所有載入影像的處理序共用區段。  
  
 **nopage**  
 將區段標記為不可分頁；適用於 Win32 裝置驅動程式。  
  
 **nocache**  
 將區段標記為不可快取；適用於 Win32 裝置驅動程式。  
  
 **discard**  
 將區段標記為可捨棄；適用於 Win32 裝置驅動程式。  
  
 **remove**  
 將區段標記為不駐留記憶體；僅限虛擬裝置驅動程式 \(V*x*D\)。  
  
 如果您未指定屬性，區段將會具有讀取和寫入屬性。  
  
## 範例  
 在下列範例中，第一個指令會識別區段及其屬性。  由於未以 `__declspec(allocate)` 宣告整數 `j`，因此不會將該整數置於 `mysec`；`j` 會包含在資料區段中。  整數 `i` 屬於 `mysec`，這是其 `__declspec(allocate)` 儲存類別屬性的結果。  
  
```  
// pragma_section.cpp  
#pragma section("mysec",read,write)  
int j = 0;  
  
__declspec(allocate("mysec"))  
int i = 0;  
  
int main(){}  
```  
  
## 請參閱  
 [Pragma 指示詞和 \_\_Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)