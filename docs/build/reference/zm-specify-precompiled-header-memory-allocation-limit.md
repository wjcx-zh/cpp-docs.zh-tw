---
title: "/Zm (指定先行編譯標頭檔的記憶體配置上限) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/zm"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pch 檔案, 記憶體配置限制"
  - "/Zm 編譯器選項 [C++]"
  - "cl.exe 編譯器, 記憶體配置限制"
  - "記憶體配置, 記憶體配置限制編譯器選項"
  - "PCH 檔案, 記憶體配置限制"
  - "先行編譯標頭檔, 記憶體配置限制"
  - "指定先行編譯標頭檔的記憶體配置上限編譯器選項"
  - "Zm 編譯器選項 [C++]"
  - "-Zm 編譯器選項 [C++]"
ms.assetid: 94c77d5e-6672-46a7-92e0-3f69e277727d
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# /Zm (指定先行編譯標頭檔的記憶體配置上限)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

判斷編譯器配置來建構先行編譯標頭檔的記憶體量。  
  
## 語法  
  
```  
/Zmfactor  
```  
  
## 引數  
 `factor`  
 縮放比例，可決定編譯器用來建構先行編譯標頭的記憶體量。  
  
 `factor` 引數是編譯器定義之工作緩衝區預設大小的百分比。  `factor` 的預設值為 100 \(百分比\)，但是您可以指定更大或更小的數目。  
  
## 備註  
 在舊版的 Visual C\+\+ 中，編譯器會使用數個離散堆積，而且每一個堆積都有限制。  因此，編譯器會視需要將堆積動態成長至總堆積大小的限制，且只有在建構先行編譯標頭檔時需要固定大小的緩衝區。  因此，通常不需要 **\/Zm** 編譯器選項。  
  
 如果編譯器的堆積空間不足，且在您使用 **\/Zm** 編譯器選項時發出 [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) 錯誤訊息，表示您可能保留過多記憶體。  請考慮移除 **\/Zm** 選項。  如果編譯器發出 [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md) 錯誤訊息，則伴隨的 [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) 訊息會指定當您使用 **\/Zm** 編譯器選項重新編譯時所用的 `factor` 引數。  
  
 下表顯示如果您假設預設的先行編譯標頭檔緩衝區大小為 75 MB 時，`factor` 引數會如何影響記憶體配置。  
  
|`factor` 的值|記憶體配置限制|  
|-----------------|-------------|  
|10|7.5 MB|  
|100|75 MB|  
|200|150 MB|  
|1000|750 MB|  
|2000|1500 MB|  
  
## 設定記憶體配置限制的其他方法  
  
#### 在 Visual Studio 開發環境中設定 \/Zm 編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  在巡覽窗格中，選取 \[**組態屬性**\]、\[**C\/C\+\+**\]、\[**命令列**\]。  
  
3.  在 \[**其他選項**\] 方塊中，輸入 **\/Zm** 編譯器選項。  
  
#### 以程式設計方式設定 \/Zm 編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)