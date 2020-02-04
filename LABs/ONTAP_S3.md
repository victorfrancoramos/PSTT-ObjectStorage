## PSTT OS DEMO_ONTAP S3 as target for FabricPool

CLUSTER2

```shell
cluster show
license show
cluster show
license add <license_code>
vserver show
vserver show -instance
net int service-policy create -policy custom-data-objects -vserver svm21 -services data-core,data-s3-server
network interface  service-policy create -policy custom-data-objects -vserver svm21 -services data-core,data-s3-server
network interface service-policy create -policy custom-data-objects -vserver svm21 -services data-core,data-s3-server
set advanced
network interface service-policy create -policy custom-data-objects -vserver svm21 -services data-core,data-s3-server
network interface show
network interface show -fields service-policy
service-policy add-service -vserver svm21 -policy custom-data-34385 -service data-s3-server
service-policy show -policy custom-data-34385
vserver object-store-server create -object-store-server server -vserver svm21
vserver object-store-server show
```

Create aggregate from the GUI
```shell
vserver object-store-server bucket create -bucket test -vserver svm21 -comment "" -aggr-list cluster2_01_SSD_1 -size 50g
vserver object-store-server show -instance
vserver object-store-server bucket show
df
vserver object-store-server user create -user s3_user -vserver svm21
vserver object-store-server user show -instance
```

CLUSTER1
Create aggregate from the GUI
```shell
storage aggregate object-store config create -object-store-name name -provider-type ONTAP_S3 -server svm21.demo.netapp.com -container-name test -is-ssl-enabled false -port 80 -ipspace Default -use-http-proxy false -access-key p3015_zzQb3A40a9Z4As2_1XL6vxiE_KC7hKcdme08xITc4y_cAhAa2gdxDcZD8rIX_0Sxvtdc39Y1R9Y3Az6BsPD7jh_BIT7X5XPPu2jP2___R3vN6kCPQxhWC7631z -secret-password Yq9H6AcRbGXi09tjD7vC4cAx6sdcMuzi6Dl11HrCj_t70Ig_p48_6HY56pgM2D3Zt3h2432TZdY7h62gP3cttA0T1o05p9kN0Q0X048y15rfgDAlF68OSfSg4Fgg0Ux
storage aggr object-store config show
storage aggr object-store config show -instance
```
