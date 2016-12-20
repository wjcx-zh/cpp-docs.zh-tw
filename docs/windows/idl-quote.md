---
title: "idl_quote | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.idl_quote"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "idl_quote attribute"
ms.assetid: a370e1b7-948b-4e67-9a25-58facf24e4c9
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# idl_quote
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可讓您使用最新版的 Visual C\+\+ 中不支援的 IDL 建構，並將它們下載到產生的.idl 檔。  
  
## 語法  
  
```  
  
      [ idl_quote(  
   text  
) ]  
```  
  
#### 參數  
 *text*  
 您想要下載到產生的.idl 檔但未傳回編譯器錯誤 Visual C\+\+ 編譯器屬性名稱。  
  
## 備註  
 如果 **idl\_quote** C\+\+ 屬性作為獨立的屬性 \(與之後的分號的右括號\)，然後*文字*會置於現狀合併的.idl 檔。  如果 **idl\_quote** 的符號，適用於*文字*會放置在該符號的屬性區塊內。  
  
## 範例  
 下列程式碼將示範如何，您可以指定不受支援的屬性 \(使用**在**，支援這種\)，以及如何定義和使用未定義的.idl 建構：  
  
```  
// cpp_attr_ref_idl_quote.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLibrary")];  
  
[export]  
struct MYFLOT {  
   int i;  
};  
  
[export]  
struct MYDUB {  
   int i;  
};  
  
[idl_quote("typedef union _S1_TYPE switch (long l1) U1_TYPE { case 1024: \  
struct MYFLOT f1; case 2048: struct MYDUB d2; } S1_TYPE;") ];  
  
typedef struct _S1_TYPE {   
   long l1;   
  
union {   
   MYFLOT f1; MYDUB d2; } U1_TYPE;   
} S1_TYPE;  
  
[uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA"), object]  
__interface IStatic{  
   HRESULT Func1([idl_quote("in")] int i);  
   HRESULT func( S1_TYPE* myStruct );  
};  
```  
  
 這段程式碼會讓 MYFLOT 和 MYDUB 和*文字* ，無法放在產生的.idl 檔的項目。  *名稱* 參數的軍隊 *文字* 之前所參考的任何項目放到 *名稱*產生的.idl 檔內。  *的相依性* 參數會強制相依性清單定義，才能放到 *文字*產生的.idl 檔內。  
  
## 需求  
  
### 屬性內容  
  
|||  
|-|-|  
|**適用於**|全螢幕輸入|  
|**可重複**|否|  
|**必要的屬性**|None|  
|**無效的屬性**|None|  
  
 如需詳細資訊，請參閱[屬性內容](../windows/attribute-contexts.md)。  
  
## 請參閱  
 [IDL Attributes](../windows/idl-attributes.md)   
 [Stand\-Alone Attributes](../windows/stand-alone-attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)