# Metricas uteis do node_exporter

## listar instancia e quantidade de CPU:
Utilizado para relatório de instancia e cpu.
```
sort_desc(count(node_cpu_seconds_total{mode="user"}) by (instance))
```

## Contagem de toda memória alocada em maquinas monitoradas ( GB)
Utilizado para saber quanto de memória já foi alocado.
```
sum(node_memory_MemTotal_bytes)/1024/1024/1024
```

## Contagem da memória livre alocada (GB)
Utilizado para saber quanto de memória total alocada não está em uso.
```
sum(node_memory_MemFree_bytes)/1024/1024/1024
```

## Lista origem nfs e quantidade de lugares montados
Utilizado para saber quantos clientes estão montando um determinado nfs.
```
sort_desc(count(node_filesystem_avail_bytes{fstype=~"nfs.*"}) by (device))
```


## Percentual de swap usado.
Mostra maquinas que usam swap.
```
sort_desc( ( node_memory_SwapTotal_bytes - node_memory_SwapFree_bytes )/ node_memory_SwapTotal_bytes *100 >0 )
```
