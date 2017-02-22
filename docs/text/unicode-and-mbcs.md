---
title: "Unicode 和 MBCS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "MBCS [C++]，Unicode"
  - "MFC [C++]，字元集"
  - "字元集 [C++]，多位元組"
  - "執行階段程式庫 [C++]，語言可移植性"
  - "字元集 [C++]，Unicode"
  - "Unicode [C++]，MFC 與 C 執行階段函式"
  - "多位元組字元 [C++]"
  - "執行階段 [C++]，語言可移植性"
ms.assetid: 677baec6-71b4-4579-94df-64f18bc117c4
caps.latest.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 9
---
# Unicode 和 MBCS
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以使用 Microsoft Foundation Class \(MFC\) 程式庫、Visual C\+\+ 的 C 執行階段程式庫和 Visual C\+\+ 開發環境，協助您開發設計國際化程式。  它們提供：  
  
-   支援 Windows 2000 \(先前是 Windows NT\) 上的 Unicode 標準。  Unicode 是現行標準，應該盡可能使用之。  
  
     Unicode 的編碼是 16 位元字元，為所有語言提供足夠的編碼。  所有的 ASCII 字元都是以加寬字元包含在 Unicode 中。  
  
    > [!NOTE]
    >  Windows 95、Windows 98 或 Windows Millennium Edition 不支援 Unicode 標準。  
  
-   在所有平台上都支援稱為雙位元組字元集 \(Double Byte Character Set，DBCS\) 的多位元組字元集 \(MBCS\) 形式。  
  
     DBCS 字元是由 1 或 2 個位元組所組成。  某些範圍的位元組當做前導位元組 \(Lead Byte\) 來使用。  前導位元組指定它自身和之後的後隨位元組 \(Trail Byte\) 組成單一 2 位元組寬的字元。  您必須保持記錄哪些位元組是前導位元組。  在特殊的多位元組字元集裡，前導位元組落在某些範圍，後隨位元組也一樣。  當這些範圍重疊時，可能需要評估內容，以決定給定位元組是做為前導位元組還是後隨位元組。  
  
-   支援可簡化國際化 MBCS 應用程式設計的工具。  
  
     執行於支援 MBCS 的 Windows 作業系統版本時，Visual C\+\+ 開發系統 \(包含整合的原始程式碼編輯器、偵錯工具和命令列工具\) 也完全支援 MBCS。  如需詳細資訊，請參閱 [Visual C\+\+ 中的 MBCS 支援](../text/mbcs-support-in-visual-cpp.md)。  
  
> [!NOTE]
>  在這份文件中，MBCS 是用來描述多位元組字元的所有非 Unicode 支援。  Visual C\+\+ 裡，MBCS 永遠是指 DBCS。  不支援大於 2 個位元組的字元集。  
  
 根據預設，ASCII 字元集是所有多位元組字元集的子集。  在許多多位元組字元集中，範圍 0x00 – 0x7F 內的每一字元與 ASCII 字元集裡有同樣值的字元完全相同。  例如，在 ASCII 和 MBCS 字元字串中，1 個位元 **NULL** 字元 \('\\0'\) 的值是 0x00，並且表示終止的 null 字元。  
  
## 請參閱  
 [文字和字串](../text/text-and-strings-in-visual-cpp.md)   
 [啟用國際化](../text/international-enabling.md)