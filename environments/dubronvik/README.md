### Reproducing Our Main Results for Dubrovnik

Install the ESAC c++ extension (if not done before):

```
/code/esac> python setup.py install
```

Setup the dataset (if not done before):

```
/datasets> python setup_dubrovnik.py
```

Train ESAC (with 10 experts):

```
/environments/dubrovnik> python ../../code/init_gating.py -c 10 -it 5000000
/environments/dubrovnik> python ../../code/init_expert.py -c 10 -e <0 to 9>
/environments/dubrovnik> python ../../code/ref_expert.py -c 10 -e <0 to 9>
/environments/dubrovnik> python ../../code/train_esac.py -c 10 -ref -maxe 5
```

Test ESAC (with 10 experts):
```
/environments/dubrovnik> python ../../code/test_esac.py -c 10
```

Test pre-trained models (with 10/20/50 experts):
```
/environments/dubrovnik> sh dl_pretrained_model.sh
/environments/dubrovnik> python ../../code/test_esac.py -c 10 -sid c10_pretrained
/environments/dubrovnik> python ../../code/test_esac.py -c 20 -sid c20_pretrained
/environments/dubrovnik> python ../../code/test_esac.py -c 50 -sid c50_pretrained
```

