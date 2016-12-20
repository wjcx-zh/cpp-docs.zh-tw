---
title: "如何：從背景執行緒取得服務 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "多執行緒, 服務"
ms.assetid: 97a56709-66d4-431a-ae63-392ee5898511
caps.latest.revision: 8
caps.handback.revision: 8
manager: "douge"
---
# 如何：從背景執行緒取得服務 (C++)
無法取得服務，藉由`IServiceProvider.QueryService`從背景執行緒。  如果您使用`QueryService`以取得服務，在主執行緒上，然後再使用背景執行緒上的服務，它也會失敗。  
  
 若要從背景執行緒中取得服務，請使用`CoMarshalInterThreadInterfaceInStream`在`IVsPackage.SetSite`方法來封送到資料流的主執行緒上的服務提供者。  您可以在背景執行緒上的服務提供者解封送處理然後用它來取得服務。  您可以一次解封送處理，因此快取所得到的介面。  
  
> [!NOTE]
>  Managed 程式碼自動封送處理執行緒，以便從背景執行緒中取得服務不需要特殊的程式碼之間的介面。  
  
## 範例  
 下列程式碼封送處理主執行緒中的服務提供者，並提供`QueryServiceFromBackgroundThread`以解封送處理從背景執行緒中取得服務的服務提供者的方法。  
  
```  
class CMyPackage : public IVsPackage  
{  
private:  
    // Used to marshal IServiceProvider between threads  
    CComPtr< IStream > m_pSPStream;  
    // IServiceProvider proxy for the background thread  
    CComPtr< IServiceProvider > m_pBackgroundSP;  
  
public:  
    HRESULT SetSite( IServiceProvider* pSP )  
    {  
        // Marshal the service provider into a stream so that  
        // the background thread can retrieve it later  
        CoMarshalInterThreadInterfaceInStream(  
            IID_IServiceProvider, pSP, &m_pSPStream);  
  
        //... do the rest of your initialization  
    }  
  
    // Call this when your background thread needs to call QueryService  
    // The first time through, it unmarshals the interface stored   
    HRESULT QueryServiceFromBackgroundThread(  
        REFGUID rsid,        // [in] Service ID  
        REFIID riid,         // [in] Interface ID  
        // [out] Interface pointer of requested service (NULL on error)  
        void **ppvObj  
    {  
        if( !m_pBackgroundSP )  
        {  
            if( !m_pSPStream )  
            {  
                return E_UNEXPECTED;  
            }  
  
            HRESULT hr = CoGetInterfaceAndReleaseStream(   
                m_pSPStream, IID_IServiceProvider,   
                (void **)&m_pBackgroundSP );  
            if( FAILED(hr) )  
            {  
                return hr;  
            }  
  
            // The CoGetInterfaceAndReleaseStream has already   
            // destroyed the stream.  To avoid double-freeing,   
            // the smart wrapper needs to be detached.  
            m_pSPStream.Detach();  
        }  
  
        return m_pBackgroundSP->QueryService( rsid, riid, ppvObj );  
    }  
};  
```  
  
## 請參閱  
 [使用並提供服務](../Topic/Using%20and%20Providing%20Services.md)   
 [服務的基本資訊](../Topic/Service%20Essentials.md)