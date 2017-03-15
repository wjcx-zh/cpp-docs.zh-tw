---
title: "idl_module | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.idl_module"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "idl_module attribute"
ms.assetid: 3578b337-e38a-4334-b747-15404c02dbc0
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# idl_module
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定.dll 檔案中的進入點。  
  
## 語法  
  
```  
  
      [ idl_module (   
   name=module_name,   
   dllname=dll,   
   uuid="uuid",   
   helpstring="help text",   
   helpstringcontext=helpcontextID,   
   helpcontext=helpcontext,   
   hidden,   
   restricted  
) ]  
function declaration  
```  
  
#### 參數  
 **名稱**  
 會顯示於.idl 檔案的程式碼區塊是使用者定義名稱。  
  
 **dllname** \(可省略\)  
 包含匯出的.dll 檔案。  
  
 `uuid` \(選擇項\)  
 唯一的 ID。  
  
 **helpstring** \(可省略\)  
 字元字串，用來描述型別程式庫。  
  
 **helpstringcontext** \(可省略\)  
 隨附.hlp 或.chm 檔中的 \[說明\] 主題的識別碼。  
  
 **helpcontext** \(可省略\)  
 這個型別程式庫說明 ID。  
  
 **隱藏** \(可省略\)  
 避免文件庫顯示為參數。  請參閱[隱藏](http://msdn.microsoft.com/library/windows/desktop/aa366861) MIDL 屬性，如需詳細資訊。  
  
 ***限制***  \(可省略\)  
 文件庫的成員無法被任意呼叫。  請參閱[限制](http://msdn.microsoft.com/library/windows/desktop/aa367157) MIDL 屬性，如需詳細資訊。  
  
 *函式宣告*  
 您會定義函式。  
  
## 備註  
 `idl_module` C \+ \+ 屬性可讓您在.dll 檔案中，它可讓您的.dll 檔案匯入指定的進入點。  
  
 **Idl\_module** 屬性具有類似的功能 [模組](http://msdn.microsoft.com/library/windows/desktop/aa367099) MIDL 屬性。  
  
 您可以匯出的任何項目從一個 COM 物件，您可以匯出.dll 檔案中，將 DLL 的進入點放在文件庫的區塊.idl 檔。  
  
 您必須使用`idl_module`在兩個步驟。  首先，您必須定義的名稱或 DLL 組。  然後，當您使用`idl_module`來指定進入點，請指定名稱和任何其他的屬性。  
  
## 範例  
 下列程式碼示範如何使用`idl_module`屬性：  
  
```  
// cpp_attr_ref_idl_module.cpp  
// compile with: /LD  
[idl_quote("midl_pragma warning(disable:2461)")];  
[module(name="MyLibrary"), idl_module(name="MyLib", dllname="xxx.dll")];  
[idl_module(name="MyLib"), entry(4), usesgetlasterror]  
void FuncName(int i);  
```  
  
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
 [entry](../windows/entry.md)   
 [Attributes Samples](http://msdn.microsoft.com/zh-tw/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)