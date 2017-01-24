---
title: "多位元組字元集 (MBCS) 的支援 | Microsoft Docs"
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
  - "_mbcs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "字元集 [C++], 多位元組"
  - "MBCS [C++]"
  - "MBCS [C++], 關於 MBCS"
  - "多位元組字元 [C++]"
ms.assetid: b498733c-a1e1-45e3-8f26-d6da3cb5f2dd
caps.latest.revision: 11
caps.handback.revision: 11
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# 多位元組字元集 (MBCS) 的支援
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

多位元組字元集 \(Multibyte Character Set，MBCS\) 是支援字元集的舊方法，例如不能以單一位元組表示的日文和中文。  如果您進行新開發，除了使用者看不見的系統字串之外，您應該對所有文字字串使用 Unicode。  MBCS 是舊版技術，不建議用於新開發。  
  
 最常見的 MBCS 實作是雙位元組字元集 \(DBCS\)。  一般而言，Visual C\+\+ 尤其是 MFC，已完全支援 DBCS。  
  
> [!WARNING]
>  在 Visual Studio 2013 \(含\) 以後版本，多位元組字元編碼 \(MBCS\) 的 MFC 程式庫將做為 Visual Studio 附加元件提供，而且 Visual Studio 客戶 \(僅限 Professional 和 Enterprise\) 可從 MSDN 下載網站免費取用。  
>   
>  程式庫大約需要 440 MB 磁碟空間，安裝包含所有當地語系化版本的程式庫。  您可以將它安裝在已安裝 Visual Studio Community、Professional 或 Enterprise Edition，且已啟用現有 \(in\-box\) MFC 功能的任何電腦。  
>   
>  如果您解除安裝或修復 Visual Studio，MBCS 程式庫也會解除安裝或修復。  然而，如果您只移除 MFC 功能，MBCS 程式庫會留在系統中。  如果您修復 MBCS 程式庫，Visual Studio 不會以任何方式修改。  
>   
>  Visual Studio 2013 \(含\) 以後版本的可轉散發套件將持續包含 MBCS MFC DLL。  將 DLL 檔案轉散發給客戶不需要任何其他步驟。  
  
 如需範例，請參閱 MFC 原始程式碼檔案。  
  
 對於其語言使用大型字元集的市場中使用的平台，Unicode 的最佳替代方案是 MBCS。  MFC 使用可國際語系化的資料類型和 C 執行階段函式來支援 MBCS。  您應該在您的相同程式碼中執行相同動作。  
  
 在 MBCS 下，字元會以 1 或 2 個位元組編碼。  在 2 個位元組的字元中，第一個或前導位元組表示它和下一個位元組會解譯成一個字元。  第一個位元組來自一個範圍的字碼，保留供做為前導位元組使用。  哪個範圍的位元組可以做為前導位元組，取決於使用中的字碼頁。  例如，日文的字碼頁 932 使用範圍 0x81 到 0x9F 來當做前導位元組，但韓文字碼頁 949 使用不同的範圍。  
  
 請在您的 MBCS 程式設計中考慮以下所有項目。  
  
 環境中的 MBCS 字元  
 MBCS 字元可出現在字串中，例如檔案和目錄名稱。  
  
 編輯作業  
 MBCS 應用程式中的編輯作業，應該可對字元而不是位元組運作。  插入號不應分割字元，而向右鍵應該能右移一個字元，依此類推。  **刪除**應該刪除字元；**復原**該重新插入。  
  
 字串處理  
 在使用 MBCS 的應用程式中，字串處理會造成特殊的問題。  在單一字串中會混用這兩種寬度的字元；因此，您必須記得檢查前導位元組。  
  
 執行階段程式庫支援  
 C 執行階段程式庫和 MFC 支援單一位元組、MBCS 和 Unicode 程式設計。  單一位元組字串是使用執行階段函式的 `str` 系列處理，MBCS 字串是使用對應的處理 `_mbs` 函式處理，而 Unicode 字串則是使用對應的 *wcs* 函式處理。  MFC 類別成員函式實作會使用可攜式執行階段，在正確的情況下，其會將函式對應至函式的正常 `str` 系列、MBCS 函式或 Unicode 函式，如「MBCS\/Unicode 可攜性」中所述。  
  
 MBCS\/Unicode 可攜性  
 使用 Tchar.h 標頭檔，您可以從相同來源建置單一位元組、MBCS 和 Unicode 應用程式。  Tchar.h 會在定義的巨集前面加上 *\_tcs*，其對應至 `str`、`_mbs` 或 *wcs* 函式 \(如適當\)。  若要建立 MBCS，請定義符號 **\_MBCS**。  若要建置 Unicode，請定義符號 **\_UNICODE**。  根據預設，會為 MFC 應用程式定義 **\_MBCS**。  如需詳細資訊，請參閱 [Tchar.h 中的泛型文字對應](../text/generic-text-mappings-in-tchar-h.md)。  
  
> [!NOTE]
>  如果您同時定義 **\_UNICODE** 和 **\_MBCS**，行為是未定義的。  
  
 Mbctype.h 和 Mbstring.h 標頭檔會定義 MBCS 特有的函式和巨集，在某些情況下您可能需要。  例如，`_ismbblead` 會告訴您在字串中的特定位元組是否為前導位元組。  
  
 針對國際可攜性，請使用 [Unicode](../text/support-for-unicode.md) 或多位元組字元集 \(MBCS\) 編寫程式。  
  
## 請您指定選項。  
  
-   [在我的程式中啟用 MBCS](../text/international-enabling.md)  
  
-   [在程式中啟用 Unicode 和 MBCS](../text/internationalization-strategies.md)  
  
-   [使用 MBCS 來建立國際化程式](../text/mbcs-programming-tips.md)  
  
-   [請參閱 MBCS 程式設計的摘要](../text/mbcs-programming-tips.md)  
  
-   [了解位元組寬度可移植性的一般文字對應](../text/generic-text-mappings-in-tchar-h.md)  
  
## 請參閱  
 [文字和字串](../text/text-and-strings-in-visual-cpp.md)   
 [Visual C\+\+ 中的 MBCS 支援](../text/mbcs-support-in-visual-cpp.md)