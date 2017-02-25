---
title: "Exporting String Classes Using CStringT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStringT class, exporting strings"
ms.assetid: bdfc441e-8d2a-461c-9885-46178066c09f
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Exporting String Classes Using CStringT
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在過去， MFC 開發人員從 `CString` 衍生特製化自己的資料類別。  Microsoft Visual C\+\+ .NET \(MFC 8.0\)， [CString](../atl-mfc-shared/using-cstring.md) 類別所呼叫的 [CStringT](../atl-mfc-shared/reference/cstringt-class.md)樣板類別取代。  這提供了幾項優點:  
  
-   允許 MFC `CString` 類別用於 ATL 專案，而不需要連接在較大的 MFC 靜態程式庫或 DLL。  
  
-   新的 `CStringT` 樣板類別，您可以自訂 `CString` 行為使用指定配置特性的樣板參數，類似於範本中標準樣板程式庫 \(STL\) \(STL\) 中。  
  
-   使用 `CStringT`時，在您從 DLL 匯出的資料類別，編譯器也會自動匯出 `CString` 基底類別。  因為 `CString` 本身是樣板類別，因為它可能是由編譯器產生，當使用，，除非編譯器知道 `CString` 從 DLL 匯入。  如果您從移轉至 Visual C\+\+ 6.0 中的專案加入至 Visual C\+\+ .NET 中，您可以乘上所定義的 `CString` 已經有提供連結器符號錯誤因為 DLL 和正確具版本匯入的 `CString` 的衝突。  適當的作法說明如下。  如需這個問題的詳細資訊，請參閱知識庫文件， 「連結錯誤，當您匯入 CString 衍生類別」\(CString\-Derived\) 在 MSDN Library CD\-ROM 或是在 [http:\/\/support.microsoft.com\/default.aspx](http://support.microsoft.com/default.aspx)。  
  
 下列情況會造成連結器產生符號錯誤為乘上所定義的類別。  舉例來說，假設您匯出 `CString`衍生類別 \(`CMyString`\) 從 MFC 擴充 DLL:  
  
 [!code-cpp[NVC_MFC_DLL#6](../atl-mfc-shared/codesnippet/CPP/exporting-string-classes-using-cstringt_1.cpp)]  
  
 消費者程式碼使用 `CString` 和 `CMyString`混合。「  MyString.h」在先行編譯標頭並不包含，，並 `CString` 陣列用法沒有可見的 `CMyString` 。  
  
 舉例來說，假設您在不同的原始程式檔， Source1.cpp 和 Source2.cpp 使用 `CString` 和 `CMyString` 類別。  在 Source1.cpp，您使用 `CMyString` 和 \#include MyString.h。  在 Source2.cpp，您使用 `CString`，但是， MyString.h \#include。  在此情況下，連結器將會是 `CStringT` 抱怨的多重定義。  這是由編譯器匯入與匯出的 DLL 和 `CMyString`正確具的 `CString` 造成的傳遞 `CStringT` 範本。  
  
 若要解決這個問題，請執行下列步驟:  
  
 匯出 `CStringA` 和 `CStringW` \(和必要的基底類別\) 與 MF C90 .dll。  包含 MFC 專案是在上一個 MFC 實作一律會使用 MFC DLL 匯出的 `CStringA` 和 `CStringW`。  
  
 使用 `CStringT` 範本，然後建立可匯出衍生類別，在中，當 `CStringT_Exported` 底下，例如:  
  
 [!code-cpp[NVC_MFC_DLL#7](../atl-mfc-shared/codesnippet/CPP/exporting-string-classes-using-cstringt_2.cpp)]  
  
 在 AfxStr.h，取代先前 `CString`、 `CStringA`和 `CStringW` typedef 如下所示:  
  
 [!code-cpp[NVC_MFC_DLL#8](../atl-mfc-shared/codesnippet/CPP/exporting-string-classes-using-cstringt_3.cpp)]  
  
 有幾個警告:  
  
-   因為這會導致 ATL 專案匯出特殊 `CStringT` 類別，您不應匯出 `CStringT` 。  
  
-   使用從 `CStringT` 的可匯出衍生類別將需要重新實作 `CStringT` 功能。  其他程式碼限制成轉送至 `CStringT` 基底類別的建構函式。  
  
-   當您以共用的 MFC DLL 時，建置`CString`、 `CStringA`和 `CStringW` 只應標記為 `__declspec(dllexport/dllimport)` 。  如果連結至 MFC 靜態程式庫，您不應該將這些類別為匯出;否則，會 `CString`、 `CStringA`和 `CStringW` 的內部使用在使用者 DLL 內將會指示 `CString` 為匯出。  
  
## 相關主題  
 [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md)  
  
## 請參閱  
 [Using CStringT](../atl-mfc-shared/using-cstringt.md)   
 [Using CString](../atl-mfc-shared/using-cstring.md)