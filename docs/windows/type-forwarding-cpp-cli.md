---
title: "類型轉送 (C + + /CLI) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- type forwarding, Visual C++
ms.assetid: ae730b69-0c27-41cc-84e1-3132783866ea
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6898c011a4e2e907cd745ccb206b0e0f0b37e78f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="type-forwarding-ccli"></a>類型轉送 (C++/CLI)
*類型轉送*可讓您進入類型一個組件 （A） 從另一個組件 （B），這樣就表示您不需要重新編譯使用組件 a 的用戶端  
  
## <a name="all-platforms"></a>所有平台  
 在所有執行階段不支援此功能。  
  
## <a name="windows-runtime"></a>Windows 執行階段  
 Windows 執行階段中不支援此功能。  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime  
 下列程式碼範例示範如何使用類型轉送。  
  
### <a name="syntax"></a>語法  
  
```  
#using "new.dll"  
[assembly:TypeForwardedTo(type::typeid)];  
```  
  
### <a name="parameters"></a>參數  
 `new`  
 組件，其中您要移動的型別定義。  
  
 `type`  
 類型為其定義您要移動到另一個組件。  
  
### <a name="remarks"></a>備註  
 元件 （組件） 隨附後的用戶端應用程式正在使用，您可以使用類型轉送到將類型從元件 （組件） 移至另一個組件中，隨附於更新的元件 （和任何所需的其他組件），以及用戶端應用程式仍然運作時不重新編譯。  
  
 類型轉送僅適用於現有的應用程式所參考的元件。 當您重建應用程式時，必須是應用程式中使用任何類型的適當的組件參考。  
  
 當從組件轉送類型 （A），您必須新增`TypeForwardedTo`該型別，以及組件參考的屬性。 您參考的組件必須包含下列其中一項：  
  
-   A.類型定義  
  
-   A`TypeForwardedTo`類型 A 的組件參考的屬性。  
  
 可以轉送的類型的範例包括：  
  
-   ref 類別  
  
-   實值類別  
  
-   列舉  
  
-   介面  
  
 您無法轉送下列類型：  
  
-   泛型類型  
  
-   原生類型  
  
-   巢狀類型 （如果您想要轉寄的巢狀的類型，您應該轉送封入類型）  
  
 您可以將類型轉送至組件中任何以 common language runtime 為目標的語言撰寫。  
  
 因此，如果用來建置組件 A.dll 原始程式碼檔中包含的類型定義 (`ref class MyClass`)，而且您想要將該類型移至 B.dll 的組件的定義，您會：  
  
1.  移動`MyClass`類型定義用來建置 B.dll 來源的程式碼檔案。  
  
2.  建置組件 B.dll  
  
3.  刪除`MyClass`類型定義用來建立 A.dll，並取代為下列的原始程式碼：  
  
    ```  
    #using "B.dll"  
    [assembly:TypeForwardedTo(MyClass::typeid)];  
    ```  
  
4.  建置組件 A.dll。  
  
5.  使用 A.dll 不需要重新編譯用戶端應用程式。  
  
### <a name="requirements"></a>需求  
 編譯器選項： **/clr**