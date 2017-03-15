---
title: "/vd (停用建構替代) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/vd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/vd0 編譯器選項 [C++]"
  - "/vd1 編譯器選項 [C++]"
  - "/vdn (停用建構替代) 編譯器選項"
  - "建構函式替代"
  - "停用建構替代編譯器選項"
  - "displacements 編譯器選項"
  - "vd0 編譯器選項 [C++]"
  - "-vd0 編譯器選項 [C++]"
  - "vd1 編譯器選項 [C++]"
  - "-vd1 編譯器選項 [C++]"
  - "vtordisp 欄位"
ms.assetid: 93258964-14d7-4b1c-9cbc-d6f4d74eab69
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# /vd (停用建構替代)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
/vdn  
```  
  
## Arguments  
 `0`  
 抑制 vtordisp 建構函式\/解構函式替代成員。  如果您確定所有類別建構函式和解構函式都會實際呼叫虛擬函式時才可選擇這個選項。  
  
 `1`  
 啟用建立隱藏 vtordisp 建構函式\/解構函式替代成員。  這個選項是預設值。  
  
 `2`  
 可以讓您在正進行建構的物件上使用 [dynamic\_cast 運算子](../../cpp/dynamic-cast-operator.md)。  例如，從虛擬基底類別到衍生類別的 dynamic\_cast。  
  
 如果您有虛擬基底加上虛擬函式，**\/vd2** 可加入 vtordisp 欄位；  但 **\/vd1** 應該就已足夠。  必須要有 **\/vd2** 的最常見情況是：當虛擬基底中唯一的虛擬函式是解構函式時。  
  
## 備註  
 這些選項僅適用於使用虛擬基底的 C\+\+ 程式碼。  
  
 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] 會在使用虛擬繼承 \(Virtual Inheritance\) 的情況下實作 C\+\+ 建構替代支援。  建構替代可以解決在建構進一步的衍生類別 \(Derived Class\) 時從建構函式呼叫某個 \(在虛擬基底中宣告並且在衍生類別中覆寫的\) 虛擬函式而產生的問題。  
  
 這個問題在由於對類別 \(Class\) 虛擬基底的替代和對其衍生類別的替代間產生不一致現象，可能會造成傳遞給虛擬函式不正確的 `this` 指標。  這個方案對類別的每一虛擬基底提供了單一建構替代調整，稱為 vtordisp 欄位。  
  
 根據預設，只要程式碼定義使用者定義的建構函式和解構函式並且也覆寫虛擬基底的虛擬函式時，就會採用 vtordisp 欄位。  
  
 這些選項會影響整個原始程式檔。  請對各個類別逐一使用 [vtordisp](../../preprocessor/vtordisp.md) 加以抑制，然後再重新啟用 vtordisp 欄位。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中，輸入編譯器選項。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)