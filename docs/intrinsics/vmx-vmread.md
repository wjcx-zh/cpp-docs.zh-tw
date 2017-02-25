---
title: "__vmx_vmread | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__vmx_vmread"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VMREAD 指令"
  - "內建 __vmx_vmread"
ms.assetid: 08bdd7a0-6435-4ea6-b9a0-f592d870e5aa
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# __vmx_vmread
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 讀取指定的欄位從目前的虛擬機器控制結構 \(VMCS\)，並將它放在指定的位置。  
  
## 語法  
  
```  
unsigned char __vmx_vmread(  
   size_t Field,  
   size_t *FieldValue  
);  
```  
  
#### 參數  
  
|參數|描述|  
|--------|--------|  
|\[in\] `Field`|讀取 \[VMCS\] 欄位中。|  
|\[in\] `FieldValue`|從 \[VMCS\] 欄位所指定的變數的指標，來儲存值的位置讀取`Field`參數。|  
  
## 傳回值  
  
|值|意義|  
|-------|--------|  
|0|操作順利完成。|  
|1|作業失敗，並在 \[可用的延伸狀態`VM-instruction error field`的目前的 VMCS。|  
|2|作業失敗，沒有可用的狀態。|  
  
## 備註  
 `__vmx_vmread`函式相當於`VMREAD`機器指令。  值為`Field`參數是一個 Intel 文件中所述的已編碼的欄位索引。  如需詳細資訊，搜尋文件中，"Intel 虛擬化技術規格的 ia\-32 Intel 架構，「 文件編號 C97063\-002，在[Intel 公司](http://go.microsoft.com/fwlink/?LinkId=127)網站的 url，然後請參閱 ＜ 附錄 c ＞ 文件。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__vmx_vmread`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h\>  
  
## 結束 Microsoft 特定  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)   
 [\_\_vmx\_vmwrite](../intrinsics/vmx-vmwrite.md)