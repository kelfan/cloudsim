# hierarchy 类结构图



## package/
## package/
## package/
## package/
## package/
## package/
## package/
## package/
## package/
## package/
## package/
## package/
## package/
## package/
## package/
## package/ network.datacenter
--> package/ power/ Switch
Object
  AppCloudlet
    TestBagofTaskApp
    WorkflowApp

## package/ power
Object
  SimEntity
    Datacenter
      NetworkDatacenter
      PowerDatacenter
        PowerDatacenterNonPowerAware
    DatacenterBroker
      PowerDatacenterBroker
    Switch
      AggregateSwitch
      EdgeSwitch
      RootSwitch
  Host
    HostDynamicWorkload
      PowerHost
        PowerHostUtilizationHistory
  VM
    PowerVm
  VmAllocationPolicy
    PowerVmAllocationPolicyAbstract
      PowerVmAllocationPolicyMigrationAbstract
        PowerVmAllocationPolicyMigrationInterQuartileRange
        PowerVmAllocationPolicyMigrationMedianAbsoluteDeviation
        PowerVmAllocationPolicyMigrationStaticThreshold
        PowerVmAllocationPolicyMigrationLocalRegression
          PowerVmAllocationPolicyMigrationLocalRegressionRobust
      PowerVmAllocationPolicySimple
  PowerVmSelectionPolicy
    PowerVmSelectionPolicyMaximumCorrelation
    PowerVmSelectionPolicyMinimumMigrationTime
    PowerVmSelectionPolicyMinimumUtilization
    PowerVmSelectionPolicyRandomSelection


## package/ power.lists
Object
  VimList
    PowerVmList

## package/ power.models
-> PowerModel
  PowerModelCubic
  PowerModelLinear
  PowerModelSqrt
  PowerModelSquare
  PowerModelSpecPower
    PowerModelSpecPowerHpProLiantMl110G3PentiumD930
    PowerModelSpecPowerHpProLiantMl110G4Xeon3040
    PowerModelSpecPowerHpProLiantMl110G5Xeon3075
    PowerModelSpecPowerIbmX3250XeonX3470
    PowerModelSpecPowerIbmX3250XeonX3480
    PowerModelSpecPowerIbmX3250XeonX3480
    PowerModelSpecPowerIbmX3550XeonX5675

## package/ provisioners
Object
  BwProvisioner
    BwProvisionerSimple
  Preprovisioner
    PeProvisionerSimple
  RamProvisioner
    RamProvisionerSimple
## package/ util
object
  ExecutionTimeMeasurer
  MathUtil
  WorkloadFileReader -> WorkloadModel
