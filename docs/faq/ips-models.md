---
layout: default
parent: IPS FAQ
nav_order: 1
title: Using IPS as a model
---

## Using IPS as a reference model for healthcare systems.

The IPS is designed to be a cross-border summary. Because of this, it has good enabling features and a consensus-based baseline of resources and terminologies. It is a reference specification for continuity of care in cross-border settings. Understanding the nature of IPS is important to evaluate its advantages and where it is not applicable:

{: .info-title }
IPS uses (for example) MedicationStatement for containing a patient’s “medication lists”. This is a helpful specification - instead of debating which resources to use, implementers can take the choices that are compatible with the IPS.

{: .info-title }
IPS uses SNOMED GPS. For cross-border use cases, this is great - a common, even if reduced, set of SNOMED values.
For medications, ATC is also supported. While ATC is not sufficient to identify a product, it provides a common enough classification. 

This also means that the PS has limitations - not because of its implementation, but because of its purpose. The IPS imposes a format (it is a static document with deliberately limited information) and some constraints that are adequate for cross-border, which normally may be insufficient for healthcare records and data exchange in a RESTful way.

{: .warning-title }
> Patient.name is mandatory
> 
> In the FHIR IPS specification, Patient name is mandatory. This is adequate for a continuity of care, where the patient identification is important and the name is expected there. However, some uses of the Patient resource - outside of a continuity-of-care document, may not require Patient name, or may even require it to be empty. 


{: .warning-title }
> Logical references are not supported
> 
> Some IPS resources actually exclude the use of logical references for Patients. This is deliberate (IPS is a document, and all the resources are available in the document, so they can be referenced to literally, and there’s no need for logical references). In real-life RESTful operations, in some cases there is no need to exchange the Patient resource and exchanging a logical identifier is important.

{: .warning-title }
> Using ATC (and other international codes) for medications
>
> ATC classification and even SNOMED codes have been confirmed to be insufficient to cover the full range of medications in prescriptions and dispenses. Those high-level codes are OK for now (while alternatives are being developed) and for cross-border. For EHRs and for intra-border communication, there are national drug catalogs and terminologies.


{: .warning-title}
> IPS contains only a part of the FHIR resources
> 
> IPS contains a few dozen resources. FHIR contains 150 and this number is growing. Limiting to a subset of resources means removing the support to certain data. For example details about scheduling, dispensing, workflows, etc., all of which may be important for patient safety.
 
