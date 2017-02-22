---
title: "/vmm、/vms、/vmv (一般用途表示) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/vms"
  - "/vmm"
  - "/vmv"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/vmm 編譯器選項 [C++]"
  - "/vms 編譯器選項 [C++]"
  - "/vmv 編譯器選項 [C++]"
  - "一般用途表示編譯器選項"
  - "單一繼承編譯器選項"
  - "虛擬繼承編譯器選項"
  - "vmm 編譯器選項 [C++]"
  - "-vmm 編譯器選項 [C++]"
  - "vms 編譯器選項 [C++]"
  - "-vms 編譯器選項 [C++]"
  - "vmv 編譯器選項 [C++]"
  - "-vmv 編譯器選項 [C++]"
ms.assetid: 0fcd7ae0-3031-4c62-a2a8-e154c8685dae
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /vmm、/vms、/vmv (一般用途表示)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在選取 [\/vmb、\/vmg \(表示方法\)](../../build/reference/vmb-vmg-representation-method.md) 做為[表示方法](../../build/reference/vmb-vmg-representation-method.md)時使用。  這些選項表示尚未發生類別定義的繼承模型。  
  
## 語法  
  
```  
/vmm  
/vms  
/vmv  
```  
  
## 備註  
 請參閱下表描述的選項。  
  
|選項|說明|  
|--------|--------|  
|**\/vmm**|將指向某一類別成員的指標最一般性的表示指定為使用多重繼承的指標。<br /><br /> 對應到 [\#pragma pointers\_to\_members](../../preprocessor/pointers-to-members.md) 的[繼承關鍵字](../../cpp/inheritance-keywords.md)和引數是 **multiple\_inheritance**。<br /><br /> 這種表示會比單一繼承所需要的表示大一些。<br /><br /> 如果指向其成員之指標被宣告的類別定義的繼承模型為虛擬，編譯器將會產生錯誤。|  
|**\/vms**|將指向某一類別成員的指標最一般性的表示指定為不使用繼承或使用單一繼承的指標。<br /><br /> [\#pragma pointers\_to\_members](../../preprocessor/pointers-to-members.md) 的對應[繼承關鍵字](../../cpp/inheritance-keywords.md)和引數是 **single\_inheritance**。<br /><br /> 這是指向某一類別成員之指標的最小表示。<br /><br /> 如果指向其成員之指標被宣告的類別定義的繼承模型為多重或虛擬，編譯器將會產生錯誤。|  
|**\/vmv**|將指向某一類別成員的指標最一般性的表示指定為使用虛擬繼承的指標。  它絕不會造成錯誤，而且也是預設值。<br /><br /> [\#pragma pointers\_to\_members](../../preprocessor/pointers-to-members.md) 的對應[繼承關鍵字](../../cpp/inheritance-keywords.md)和引數是 **virtual\_inheritance**。<br /><br /> 這個選項需要比其他選項更大的指標和額外程式碼來解譯指標。|  
  
 當您指定這些繼承模型選項的其中一個時，不論類別成員的繼承類型為何，或者指標是在類別之前或之後宣告，該模型都會用於所有指向這些類別成員的指標。  因此，如果您一直都是使用單一繼承類別，就可以透過 **\/vms** 編譯，縮減程式碼大小；但是，如果您要使用最一般性的情況 \(放棄最大資料表示\)，請使用  **\/vmv** 編譯。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中，輸入編譯器選項。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [\/vmb、\/vmg \(表示方法\)](../../build/reference/vmb-vmg-representation-method.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)