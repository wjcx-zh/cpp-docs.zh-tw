---
title: "Type Forwarding (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "type forwarding, Visual C++"
ms.assetid: ae730b69-0c27-41cc-84e1-3132783866ea
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Type Forwarding (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

*型別轉送* 可讓您將某個組件 \(組件 A\) 移動類型到其他組件 \(B 組件\) 的話，這個模式中，重新編譯使用組件 A 的用戶端是不必要的。  
  
## 所有平台  
 這個功能不會在所有執行階段中支援。  
  
## Windows Runtime \- Windows 執行階段  
 在[!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]中不支援此功能。  
  
### 需求  
 編譯器選項：**\/ZW**  
  
## Common Language Runtime  
 下列程式碼範例會示範如何使用型別轉送。  
  
### 語法  
  
```  
#using "new.dll"  
[assembly:TypeForwardedTo(type::typeid)];  
```  
  
### 參數  
 `new`  
 您要將型別定義的組件。  
  
 `type`  
 您要移至另一個組件的型別。  
  
### 備註  
 在和用戶端應用程式使用元件 \(組件\) 後的，您可以使用型別轉送從元件 \(組件\) 將型別的其他組件，傳輸更新元件 \(和其他組件需要\)，因此，用戶端應用程式中運作，而不需要重新編譯。  
  
 轉送元件的型別只能由現有的應用程式參考。  當您重新建置應用程式時，必須在應用程式中使用任何型別的適當的組件參考。  
  
 當型別轉送時 \(從組件中的型別 A\)，您必須加入該型別的 `TypeForwardedTo` 屬性，以及組件參考。  您參考的組件必須包含下列其中一項:  
  
-   型別 A 的定義。  
  
-   型別 A 的 `TypeForwardedTo` 屬性，以及組件參考。  
  
 可以轉送包括型別的範例:  
  
-   ref 類別  
  
-   值類別  
  
-   列舉  
  
-   介面  
  
 您無法將下列型別轉送:  
  
-   泛型型別  
  
-   原生型別。  
  
-   巢狀型別 \(如果您要轉送巢狀型別，您應該轉送封入型別\)  
  
 您可以將型別以 Common Language Runtime 轉送至任何語言撰寫的組件。  
  
 因此，如果用來建立組件 A.dll 的原始程式碼檔包含型別定義 \(`ref class MyClass`\) 和您要移動該型別定義的組件 B.dll，您可以:  
  
1.  移動 `MyClass` 型別定義來產生原始程式碼檔建置 B.dll。  
  
2.  建立組件 B.dll  
  
3.  刪除套用的原始程式碼的 `MyClass` 型別定義建置 A.dll，並以下列程式碼替代:  
  
    ```  
    #using "B.dll"  
    [assembly:TypeForwardedTo(MyClass::typeid)];  
    ```  
  
4.  建置組件 A.dll。  
  
5.  使用 A.dll，而不需重新編譯用戶端應用程式。  
  
### 需求  
 編譯器選項：**\/clr**