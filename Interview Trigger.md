public class ChildCustomSettingHandler 
{
    public static void stateWP(List<Child__c> childList)
    {
        Set<Id> parIds = new Set<Id>();
        for(Child__c chi : childList)
        {
            if(chi.Amount__c != null && chi.Parent__c != null)
            {
                parIds.add(chi.Parent__c);
            }
        }
        
        Map<Id, Parent__c> updatedparent = new Map<Id, Parent__c>([SELECT Id, States__c, Result__c 
                                                                   FROM Parent__c 
                                                                   WHERE Id IN: parIds]);
        
        List<Parent__c> parnet = new List<Parent__c>();
        
        if(!updatedparent.isEmpty())
        {
            for(Child__c chi : childList)
            {
                Parent__c existingParent = updatedparent.get(chi.Parent__c);
                
                if (existingParent != null && existingParent.States__c != null)
                {
                    SWP__c se = SWP__c.getValues(existingParent.States__c);
                    System.debug(se.Percentage__c + ' ' +  se.Name);
                    
                    Decimal result = percentageCalculate(chi.Amount__c, se.Percentage__c);
                    existingParent.Result__c = 'Rs. ' + String.valueOf(result.format());   
                    System.debug(result);
                    
                    parnet.add(existingParent);
                }
            }
        }
        
        if(!parnet.isEmpty())
        {
            update parnet;
        }
    }
    
    public static decimal percentageCalculate(Decimal Amount, Decimal percent)
    {
        return (Amount + (Amount * (percent / 100)));        
    }
}
