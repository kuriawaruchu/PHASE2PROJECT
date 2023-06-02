{
 "cells": [
  {
   "attachments": {
    "king_county.jpg": {
     "image/jpeg": "/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAoGBxQUExYTFBQWFhYZGx4aGhoaGhofIBwZGhYgGx0bGRwaHysiHx8oHx8cJDQkKCwuMTExHCE3PDcwOyswMS4BCwsLDw4PHRERHTAoIigyMDAwMDAyMDAwMjIwMjswMDAwMDAwMDAwMDAwMjAwMDAwMDAwMDAwMDAwMDAwMDAwMP/AABEIALcBEwMBIgACEQEDEQH/xAAcAAAABwEBAAAAAAAAAAAAAAAAAgMEBQYHAQj/xABSEAACAQIDBgIFBgkIBwcFAAABAgMAEQQSIQUGEzFBUSJhBzJxgZEUI0KhscEzUmJyc7Kz0fAVJDRDgpKi4RYlU3STwvE1VGNko9LURFWElMP/xAAZAQADAQEBAAAAAAAAAAAAAAAAAgMBBAX/xAAuEQACAgEDAwMEAgEFAQAAAAAAAQIRAxIhMQRBURMyYSJxgfChscEFQkOR4TP/2gAMAwEAAhEDEQA/AJq1ctSlq5avcPLCWrlqUtXLUAEtXLUpauWoMCWruWjWoWosAmWuWpS1DLRYCdqFqUtQtWWFCdqFqUy0MtbYUJ2oWpTLQy0WFCdqFqUy0MtFhQnau2pS1DLWWFCdqFqUy0LVthQnahaj2oWrLCglqrm9G05IEhkiIDmQzgk9EPDh9oIVmt+X51Y8SDlIX1msq/nuQq/4iKo++DGbEiCJfCWWKPVdVSyLoDfW3115X+p5PbBfd/g9L/Tse8pvtsRe+ezlSVZ41ywYlONGp+jm/CR/2HuNOhWoW2lbnv1uiJtnCGJbyYZQ0Xc5EAZP7Sg/2gtYeLEc/P3VwxnqVnS1TNS9D28+eP5LIfHELISecZOg/skgey1aVavNmx9pPhsRHiEFyjXI/GU6MvvUkV6I2RjhNDHMhzK6hlPcHrUM8V7hovsDbmyo8TBJh5RdJFseVweasvmDYj2V5u29smTDTyYeUWeNreRH0WHkwsR7a9OVn3po3VE+HGMjHzsK/OW+lDzJ9qHX2FvKm6fJT0szJC1ZitcYaWvpzt50Daug13EAtvOhRqFAG92oZaPauWr17PMCWoZaPauWrbCglqFqPahaiwoJauWo9qFqLALahajWoWosygtqFqNahlosKC5aFqNahaiwoLloWo1qFqLCgtqFqNau0WFBLV3LRqFqLNoLaqvvvLOkTTwTMnCZVZAF1U2zPqD6rSRD+0e1Wq1VDb+0FVouITwmQiVba5MTct15rGyW05oK4uuz6IxS7s6+kw65P4RT4t9caP6+/tSM/wDLTiPf/GDmYm9qfuIqB2ngnglkhceON2RvapsSPI8x5EUhXOss/LKvHHwaPuhvRPiWleQRhIIzICoIJla8cYOZiLXYt7VFH9H2D4+0uI1gkCmQkkWBGgub20JB9xqD2VtCLDbOGfMWxMrHw2uEhAUA6jTMxNWn0YQxyYDabqGJZWQDqRwS1hz1ux+quLLryTcpfY68bjDHSLntffnDw2EZ4zOSqlTZLgqpu9jfVh6oI5i+lVre3dyPDBpIlvnmPgYAqodeIculxZiRztRNlbmYqeNAR8mUM3rXzZW4R9XnrlcFSV72q0ekGMGKPykF/P5o/wDSp9RBQx7G4JNz3MyxBuUVsPFZ2VCctiAzAXF/bWl7mBoVkwTXY4dgEIHONtU8h1+zpVD2lALxfpI/1xWsY+RIIpcQVJ4cZYhbXKoC1h0729tc2K5qjoz1FiwRjqSFHYan4nT6vfRvkwHQG9wc2pItyN+lZbvLv3PPHE0LGCNmkDKjnMQIkYB3ABU+I6KeRBv2vu4z5sDh2PVL2uT27m/xrqeHRHUzk126Mt9IO7EWDMAhVgJeMSrEEKFcZAvYWbrfpVSJN7FATlDch19rDXyrVvS9hi8mEAFzab7Iz91Z1ioLsCQ40FrW5d+Xu59KviUpRuxZtJkdc/7JP491Cncmp0U/ChVfTYmtGu3rtq7HFajZa9azzaCWrlqUy0MtFhQnauWpW1cy1thQnahalLULUWAlahalctDLRZglahalctctRYCdqFqUtQtRYCdqFqUtXLUWBC704+aGFpIBGWQFyHBIKLbNazDUA5vYpqmR+k2cetBCfYXX7SasO/W11hyC4JDAslxchVJZSOzLIo9xrMtpYXhSyRXuEYqDpqoPhOncWPvrz59RP1Gk9kd0cMVCMn3LkfSiw54ZfdIf/ZTPf+Ao8c6ZkLi0oVj4ZsokOot9GQIO/DaoHdvACbFQQkaNIub8wHM/+EGrVj4XxhxiohvwzieXJ4nv77o8i28x2rny9RLUotl8eCOhySK3sEzz4iGDjS2kdVPzj+qT4jz/ABbmrgsHyvaUSa5XlzlTa3CTW1rcsi2qu7gxhZJ8QSqiKIhWYgASS/NLqfIufdVl3CzK+OxKNHmhg8BHiAZ2JB76BDp51zZ7lJfH+S2Gowb7s56bt3GXFpiY1us62a1vwkYAPPumX+61Z82BkHNT9VbnujPJPiAZWeVQgYswuokEQWw0AW/EY2AHI6HmKFtDc3FYvFYgRcOOFJXZpHfKq5pCLWGpACm1hYa61WM9NRl4JON7oqODwEszJFy9bLm9VRYu32E+2tr9FGyIcNhnMc6zuSJJMgFkLRj5u9yDoPcb1TsFs/ZWCIu8u0cR0WO/DvqDYg6jmDYt5irn6MsLIuGnLwiJXN0FwcwCkE6db6a2pJTbkkuBlCo2yG3i9IMsqIYC0EbZwcpHENlQrdiPB6/JSdLa9BZ/SE9oYyP9qo/9Jqz/AAWy0MXzriPKJGHK5bhQWWx636c/trQPSCt4I/0qc+/Cas6qtBuD3lK2p/V/nx/ritJ3q/oWJ/QyfqGs32qDZD+Wn64rS94r/I8Tb/Yvb+4dRXH0vJ09VyZDsfZSyCBJWMaF2JJIBI+Sxerm58jyBrVNxwvyLDhDmUIQp7jNYH6qySSG8MRPPOSb9bwRitY9H4/mGGH5LfrmvQyr6GcUfcV70t4kxthXH/ij4iOsx25j3mkDtluAFUKLAIt7KPIdyST1NaT6ah4MN+dJ9iVmEtSxcDsN8sA0K3t5j91Cm03M12ra5C6Ym3KK7akRGw+lXU05n7a9XUjzdLFbULUoE0oZKNaDSxPLXLUpahamsKE8tDLSlqFqLMErULUrauWosyhO1DLSoSjCA1jmkbpbG9qFqX4RouWjUg0iVqFqVEZPIXpPF5kR2ynwqTbzAuBQ5pcmqLMt9J0Ks6zADNco57hixiPY+BD8RVLtV921gmxEuKhQ5hHC78umHylT5khcv9s1Q7eRrysc9abflno5IaWkvCLDuSgVsRiDYCOIqp7PKRGP8Jk+FXz0XYuKFJsRMfwsnCjFvWyLnYC+gBzDmQNLVm2zNqyRwvDEPHJIrE2BuqoyhdfNia13cfd2STZ+G4x4LRyyu11sSHY2sTa1wefsqU4ap2ykZpQ0oou8+6HyXDNOsl8PNKAqj1rAyGMMCLDKLg6nW1Wz0RbDigjxfFkjfMqCSLRiioHN5AOhzHT8k86ld99mwDBwxMDJCkyHRtX0kZvEtrXuRpame4hQnaHDgWFDEpCg5jyk0LHn+8ml9T6tPyaofTqLNsneJJZvk8SBIwgZTyJHhOigWUWbrfpVF2tguJPOCTl4j6dNJGsbd/OpzclE+UB84zmMjJz8Nku1x7qY463Gn/SSftTUus2aK9KrbG8WywmAg4UTsZBiOKIlJMgAkUK5GtuVhyvbStB2Kp+TLmjMRyt4D9EXNh8KjtxZGODiVQAAHOY63Jmk0GvMWHxqdaQA+IixFr8tbEny5fZTwkmku+xKadv8mLG/AU9i37KGtL3za8MflIo/9Fz94qQwG72FiCiOBPDyLAsbkAXzPc3sBrfpTHfIgxG3SVb/APCIpupmpQpGYE1Lco22T4FPZk/WFantDC8WGWK+XOhS9r2zDLe3XnyrLNt/gx7V/WFapNm8IXQX8RHO1jf7q4+nlW51dSt0VyPcXCoqLLI7WNxdgoY5QugAvyHIGp/BRRQiOCIBVCsygEmwBA66/SNLxoBewA1+/r3rhQZr2FwOfkxufiQK6Z5nJUcqjTKH6aPwWG/Pf9UVlzjT3VqHpmf5jDG/02/UH+dZc7Cx9lPj9pjCNQokh1NCqWBumQUMgpGMOTYLS4w7dVr0dXycOleAAjuKPYeVHhw9zqBS2VVOgHt7UkpoaMGEfB6ZipA91JNB+dS020SdKS+XXFrW++lUmM4oRZPM1y1FecCkHx2vT4VWMycoDq1KQwFuVM/5QGXLcd6WG01ygDTXXzoc5VsCxqxQoRXQTSM2KDcqJhEdw+S11Gl+Rb8XyuOvSkllSjchljt1EkJY1RA76kkADuWNgPv+NKMQ4GgW2hHY/u/fVXfeAS4qLD+IFLMVItqb307ra3vNqnp1b1ksXA0HLN+ST9/n5muKXUtT3ex2R6dOGy3FMQ7A+qDppzH2VC7T2yMpjLLceMi9zaM5yCPPLl/tVC7W2zI/9Jn4Ctyggu0reTt/A7iofFzQiKTgwpHYKnrZnOZs9mcm1/m9VUm1/cGydR9DUV+TMeD6lbJHceN1E+KjCHM8cHiTmC15bAc+aAHXrcaUTfPdm5wMUELZnDLIqBVZrZTc5zYWUMdas25S/JtmxMLM7gSEHtK7MOXkbc+lNN8HMq4dzoXVmIFxzCCw8q5W9GPV8lffl0lb2NtRllhw2Egw2GlkOQyveaUHKSWzHRL2PhsRqKt+IgnGHRJJWnkjmbPI1hcBbkgdBY6CiejXZUKxGQRpxOKwz5RmtlFhm52qV28/g0uPniD53WnwSc5JiZkoqkQuOT/VeGHaXr5cQUnuamuN/Qj/APpSm2plj2XASQBxba+YkNIejPaiPPiMl2OSMEeRY669LXPuqMotdQ5disJL0a7jDcaN4sSZXR8iYZyzZTa6lTlva2aw0HWubQxHz0zHw+OQkHp84dDbS9aPtjEZImZsgFxcsbC19efPS+nXyrHNobEx+NnleDDy8F3ZlMoyCzNe4vofjVMsI5d0xMM3je5o/o4xIOBiYkDWT9s/286sYZXvpceY7+2sahmxuEi+TNOsSxlgbFRqXJNiNSLk8mFXH0VSmRJ2MjyksmrE9m5X1tz53pJKK2iNpdamXbOBzIFQO/OsC8/wi+X0XqbldUBLFUUdWIUfE6VD76i+HBuCM6nT2EVOUXpbCDWpGd7wkiLS+hXS/mK10Me38ewfvrId4tYj5EfaPqrXuIFVnN7AFtPKp4E2qLdRszpB6n4adfeaBQf9dftqjy+kgSC+Hw7Cxi/DD6Mys6kLG3ZQefIirNuxtNp8MkzlSWZhdVyjws40W5PTqa6nhko6mcimm6RXfSzgjLDh0BAJdhry/B1lRhbopI7gG32VrXpTYrDARz4pHxQisq2vE68PKrsAp0UMfpN+LpVsMbixZypob/J27H66FSmGTwJmWxyrfMDe+Uc6FdHoxE9Q1sTEDTSis5PWkWY1zjHvVdJFSF/lBHQ02nxnto+YnnSbIDWaTdQ1fFW702l2gRyvSmOkCetw1vyzOFvbnqajJZXJchoMimwbmOQOrB7X17CttJ0FNqxV9pNTaTGk9aQmxYCGTiQFQGPhNycvOwDEmoiTbotdUUj84g/3bH7ab1sceQ9LJLgn48dauTbbRCFJGZiAFHMk6DT7zUftB+ApYyJKwl4LqiSqEazXsxIZjdbXW1tTc0rurHiGXDyYcKqHFsJmzKnzY4BC3LZj9MBQTzPeoZOqT9iLQ6Zr3M5j9tTA2QxDl1ZjqRpyAvrfryPY08bfCbDYbDWtIZZJFZimoysosig2PM8+dhULBg1bEOGcpGhklb2I+cquYgAtyueV6ktv7VlwmFwnyWayyNMzHIubmPBd1NirXBta9q45ZJZKTOpY1BWkN9uYM/ynxFkIPyqMZBmFxxRc3GnI2selaLjhLHEzpEZHAGWMEAsb259gNT10qkbXQ/yiP96T6pl7fxrQ3Wdzt/ElmJAEoUEk2GdRpfQDSopauew7enjuUXG4lizBVyEk5r3LX5EEnXytyHYUzKm1ixsTexJ5jSpTaMRM0vTxt9bHtUXtGDkCQNNNDqbjSx5V0RbZFqjbNjgfydhuR+YhH+HT7aY7fS0WGH5DfWsdS+6MCtgMIH1HAiGndUBvcdKa71wXfDpmWMHiDM1yFAC20XU8gOY5ipZ3ePSvI2HbJqYpuA2XDse0rXsL/QXpUjiMdArshAlYAy2sNLFV6/SBI+NVXExrHhTFFNiJs8jC0MAALWQMGzhmAykciNfYaP6ON3HjklndJIg6hVWQnMb2LFlOi+qLW53PlRiahH5Ca1SvsOt+8NFiYYXxOJOGhHjyKhdmOW/iNsylQToO/kKrno72ci4uN8OHdVzcVyCqFSjKPW8THMR3t5Vc998KDhWF+vW34pqUwkoLyyZTdBkAN9QBmuARpr25i3lWKcpPT+7g4xjG/IaPZtp2nzXYrZQRfLyvlLdyOluZqkR7Ox2LxEsMu0JkSPNfhgJmyvltaPLp7b1PbubzTYiRC0aRxshNlOazeK3jNuYUHkOZpuhZZcaykqwinIIuCCHuCKJQlBpXyZCSkm/B3C+jPBqc0vFmOly7nXp9Cx+upHdTARwS4pIlCoGWyi9lGRjpf4++oj0ZY95YYTJJLI7RlizszDRl5s3Nifsqw7IH84xXtT9maJx0zivkIzcoSv8AdzINubSmaGOSSR3kDTMvEbiahNAFbQDQaa+wcq1beU3wMZ78M/VWZSYiBPHiImkRXl8OYfisBcaWFh361pW8J/1fGeXhi+u3766Op9jJYPeig7w/gj9f1f5Vq8+sL/mH7KyjeEHhHnoK1i/zbfmf8tcHTco7OpMN3RikdeGnMvhyF5aFZydfYL+6tc3FwzR4NY5AQyPIpv3EjjpzHn1rKth4yYJGwkJKyQtzOoIn0Leemgta1ah6PJi+BRje5kdjfncu5JOp616eX2HBH3DT0myKsOHZzZROtza9hY3Nh5XrLtrY2JpX4aNwwbAlrE3JOYixtz5faa0j0xD+aRfph+zesgM9mt3/AHVLA5V9I81HuHkxS3PgP97/ACoVxj5UKr6sxPTibfHNh2AyzxsNdRIh5C7cj05movHbxYKNirYqMkX9U5tQTp4L66HT94rEziCeYHuHPrRc7dq6NyOxtuH3swFr/KY+nrEjn5EX/dTrCbaw0wLJJEyg2LBhpflftfzrDo4zw3a3IoB/azfupHhnrpyPx5fbWAazt+JpcQqvH/NVCkMBmvK0gVbBWub57dB1vpVX3SwTrPLAFLZePkJMeUOInUEh9MunI9deQNF3N2kUilcKrCIQgq2Y5mbEooYm4IK6lRyB6d5jBYXiS4tmY2ihxDIq2C5iHjJYW10J9+tcWSTjJryd+OnGxptnASSzQxFo1kkSFGKEFMz2UkFTYrfsarU6ZdOtuflbQGrRsofObO/Nwv6y1WdoDU+wfq1Jyd0OltZbttSxyDFKkPDK40hznZ+I2WTx2IsnL1R9dN8ao/1PZQD8r5gcyXgJJ89be4U72js54/lbPFIgkxpZWbk62lsyCwsLEdTfnpVi2Tu3HisPs+V3dTh24ihbeI8QNZrg6XQcu9KpJS/fANNxKbOfFif0M320pj9mTYjZ+zeDFJLYz3yqTlDS2uxHLS/tPWn+wcCk+KeJ78N1lViDbQ+ZGlaFu/gIcPAkMGsaXAObNzYsbt3uTWRnpXybONso22v6ev8AvUf7Zamt39iTx7RmneCJY3Mlpc15GzMtgAGsF0vyBqC2z/2gvf5TF+2WtLQnTT40kZNWbNcGD7QPzsovzdtfaSCOdqbKQDzBFre/Pf7OtH2oPnpP0j/rmmtdMXRJo3Dc2MrgMKOohiB68k+zU/Go3fiHM0F+0nbunemeK2hJFsvDcN2Q8LC6qSD4po0YXGtitxSE2KeTC4KSRizsst2JJJIkC3JPsqGaL0OY+F/Woj/draq4bBSSFbjj5bA21cJ5edPl3lL4eKZMqZpjERe/q3UgFgNbjt0I86ruZRsyTOGKjFR3A53tHb67U0fEImCwt0zX2jIgueTM8oDcuh1Aq2FLSm0RzN65JFjxG0HxGzBLIQWY6kAKLgEHTpytY1aiNG/M/wCU1RdjTZ9jK1gPHILDlozCr3Hcg+aW/wANI/8A7P8AA/8Axr8mZejzGXxkUYe6tCWsB4b/ADmqm/a45dqtuyntjMRpm8Mnht3lX296qno83VxmHxmHaaBkRISrtdCAx4lhdWPccu9WjYOuOn9k31Tr91P1DqUX8iYV9Ml8f5LOPVyhQvKwHIa9NO16jtkn+c4keafqVKW191ROAe+JxKcrMjXGhOZALX7afXUnJymmx4qoyS8GV7b3Wx3DZRhpHMkktrI2ilHsTflrl1PetH3jUrs5FIswWIEdjcXFWUmoLfs/zR7nk0f7UVbLkjKNInji1JGd7dHzTeytZwq5owO6AfFbVkG2phwm9la1hZCIlIuTlTkO4W/1XrkwOnbOrqN9kU3BejeWKJIxPEbMhJyMNEz8jfW+e3LTWrVuzsY4WAQs4c5ibgZfWLNa1zyvUny6mi4qWwudBe5JNgBlPMk97V2yzKSaOJQp2Uz0xf0JP0y/qPWRqyrE0gKmXiKqqQD4MjZiR2OYD+ya1H0wbZw4wqRcVS/EVwq3bw2YX8NwKyAbQj7np0NU6duG9ef5DIlLaxb30KR+Xp3PwNdop+AtDQ3/AOtGLHnYCuzyrfTU1yNL+trbp0q2ruyWkPFKzIVAv4l16Xs3Trz91jT/AORgEg2JCa+NAbhb+y3Lwcza19aV2NhFlbLcKC6g3Atqr8wfO3xp+cQpzBhccG4v9GR4+YF7CzC/uqcsm+xWOPbceejfZZxIxUOcJcQtmsT6kwblcc8tvfVq3PhVsTiUYXVkkDDuGl1GntNV30ebTXDnESspIAiFltc55gg5+bVIYDakmHlxDR5bszg5hf1IcRILa/jRr7q5Mtyl++DpxVGI927hkhxaOihYYGguF+it7gKOuimqPtCE6ny7+VW/G4xpsM8slszphGawsLtFITYdKrGOAyH2fdUt0yq3Rqe+OE4qYeIkjNMq3FtLo2tQ27G8SYeOOCafihpjBEY4ipWRZBnVznII8a2Pt51G7CF8XjB32iB8VlFM8TsUwrsuAOjGLGygsSqBss6XsGbU/kgknpeqwgt0/j+iMpOk/uWTZu34MMYcPIsrPiJpEQqFygmfJ4yWBGrDkDVe3h3ixGEwmG+TymPiSyB7KhuAsdvWU25nlbnXdp4fPjdm+JFy4iRvEbZrYpPCvdj0FNN7tmTT4TC8GGWXLLKW4aM1gVj55Qbcj8KyMUpR+zGbdP8ABMbaf/WSj/zUX7ZaX3T23iH25iYHmkaFOLlQnwjLIoFh5A0ht7/tIf7zF+1Wnm62yXTbOJmaGdcxls7JaIqXW2ViNSbfUaTFVS/IZOxQtqH56T9I/wCuag8BHIGOfNa3U31uPOprax+el/SP+uaaE1eLpUI1uaZjp2XZmHZTY8LCi/kcRGp+IvSbMRgsDe98s3P9NVh3IxiNhoEDIxSGLMt1uLi+o5j6Nr/ldqqvpg3p4csUKozOqlr6ZfnLWFwSSfA2nspJLXHQuTIPTPU+CT3f2McXgZoA4Q/KFbMRm9RImta451KYjcRGhhh45AjxRxVyg8RJYlPWFhduevsrLt2N+cdhlbKkTqz57OhNmyhSRlZTyHc1q25G8L4zDnETIEZGkQqt7WCo17Ek399OlLFFJiyanNtDbaeyI8Ls84eJ2dVYtmbKTdy5I8IA0IIqzw3IFjbwr0/jpVe3kS2EJvbUi3mHkJPvJ+qp3CmwX8xPsNczlc3L7FdNQS+46YkgjuLfEVmeM31iwW0Zg8byfhFslrgs4cXzEcwPrFS29GzcXiZ1nwEzhVXhuElygkEtoMwBNmGvkOdVKT0Z7Q4pmZBI7cyzx9rdWOvnXRGKlTkyTk42kixSemLDgkfJ5r8iM0ffuCad7hbzpi8ZiiBkzRxOqswJI1B5dvD/AHhVYPo2xIUl4UAA1OdABbW9ywqKyHDTwvG5V+IiMyNa6cRfDmXQr5DQj41rjDhcmLUboT/Hvqiel7bRiw6qrobuOLHcZ7aMp53VbjtqSuve44mZY1LOQoHMm/8ABrMdubiYzFvJMqRhZS75xL66OwMWZTYDLGFX3H3yxVJ7jTtLYzPau13ma4LKLWy5j8baDW/1VPYHe/aCoY1nmy5Qq/OG62/FvrysPdU5h/RPjV/q4f74p/gvR1j4yDkh/viuhyilSROpSdsquI21j5CxMs5DdDLIQCbagZrCxFx01PSmbriGIJXUdTqT4ri9+1z7ia1OHdDE/SSP3MKNJubiSeSAW6NY363Ivpy5W+ukWV+B3CPkyHaCsImVhaxHkBre1vgAByqEy1bd6MPI8rRKFVInZLd2Vipb4g2/zqGGyZfyfj/lXTFtrcjJb7EXlNCpT+SJe6/3j+6uVtiiMKdKULdKTi1pR4rAa0jHXBJbGBJIFySV0HkT09lPWiJZgLfgFb3BM32U03cxPDJPZlN9NPC4vr52pbamIMXzuZCzxJGY+qhospOh15aHlrU3eorH2ktuVs9p1xESi5JgOlvVXEKzc9NACamtmbHbEy4lUZQVLHW9jnhxEQ5DvID7AahvRbvDDFOwfMHksqgC401HLrz+FTG7O1+BJiXKMQ5IsPWUIc2bzvxNPZUMmpSLQScQY7DmLDPESCY1wqEjqVikBIv0uNKrGNbw+77qse+G0GCYh2jKKzwkE2OgEgtZTfqKo0u0s6nLr09U0qi5bjOSjszZMVsdIJY3R5G4uLWQq7XVSc5IjFhYEk6a0vs7CQyKTLGjsuLn4ZZQSridmupt4TZOflUFFvGcTHh5BNh1dHSRkzgkHLYqRfQi9NIN5EjZ1lm4REs8gADEEiZ2GoFrcxfra19DWLVuDirW5a93NmQSIJJIo3eOaUxsyglCJb3UnkbgHTtRtwWvhf7Z/VWq5u7vDDHxU+Vx/hWZc7ICcyqx0NtM16q2K2m2DxYUTFoFYMwjscw4Y6cr3IvrSqMm68DNRq75LFvAw/lEf7xD+0StMvWJY/F4CSYOMROkocFi6FrurCzEg2FreypLeLeieGGOaDFmXMzKRw0X1edwRf8AjzrVjlskjJNVbfBX8dhJJMTJGiMztI1hbU3c259Dfn5ilm3PxgNmw8yC+rZLhQebEjSw51Dz7WxGKm4mrTMADwxY5V7Ac9AOVSxxeNwwI4mIzSFFjEhdSLOSSyOxC8hbX6V66UmtnyRdPdcFj9H2IlixUyCMq00fhEgZcojX5uwOpFiASPKrDvJgsI8uHXE4dppZbR8RZCLMLDkTot2uBWYbM3tngdZ0WJncHVwxtzZrBXFgdOfYdqm8BvliMdPERFCrQZpebgNlym3Uj1R8aWcJp2jYuDjRNbd3UZLnC4aUqunjlj1b8kEgWHe558qsHo9wk0WCeOdDHIZW8NwfDIVtqpIPPvWZY7askm045CxHEMLkK7FfGimw7gXA9optu7vBjipjixE5ZiiIucteR3FrZzb1VYe+h45SjyLcUzYt7z/NW/SN+s9LYjbsOGWEzyrErxqAWJ9YAafAk+6slh2/jZ45YpMS5VI5JbFY9XjBaxOW+pJphtnbc+JwgaeTOY5VRDlRbLwjp4FF/fU44HdtjuW1GwYfePZYj4SYrDqmhI4gF7W5km5va1zVch2hhX2hLnxdsNl8JXEukYfLFYBkkAufnNL9G7VjpnYE+X76sGz8I52fNObZGnjjHfNHG7NcdrSL9dUeDTvbEjOzX44dmtyxYa+lvl0jA3FtVaYqfeDVF3q2nFg8WrwQRShiGRpGkfKUyn5sh7AEk30rOHGtXeTApiUhIBjWPBPIFBveSIC7Ekcm006W0rfSUXbdmqWpMfbQ9Ks8yFJYISLhgFMguQeROe4Fu1c216TJJMPHFFGsXht808kZiZbqFGU6raxHtta4qmNDT7ZOxxJh8VMSQYeEQBax4jlTfroB0oSglwFMdYTfeZVs74p2ufEMZOvsFgSNKWG/L8s2MH/5033rVTcan2/uoctarSEtmi4zbwhxcuGmxeMjSMkcQ4uY5iACBljjYgkH2aVPbPwwmUPHjtpup5MkshB8ruq2Pkazz0kD+f4kj8cfs1rQ9y9k7MmhXgLiJcpAk+dmjAfh5iqgyIpJbXS+nak9PVFNMyU3F/8AhG4jdLCOxLTbQgJJYvKAcxNydAS1763I+2uf6HYCxIxGPlYDQIlge3OI6HTXzq6R4ODiCJcLOzENlzyRsCqWBPilaw1HO17jS9LwDKoVcIjMCCueU8iSeeR2sNNOXTS1qzTkrkk579jO/wDR9f8Aus/vxij6uBpQrQcz9MFg/wDjyf8Ax6FZon5/hm38/wAnn/DwMuYsG0Glvb+VbpTlcTGVF0Ynqc4HU6WynpXXw4iW2biKSGPhFrggajNrcefSkeEOjActCfKuyle5OWqtjrEG4AIvpYam1xzIH8Xpq5uAT2t7NCalMDCjRSmR7GNSUIANyW0HbsO+tMYog+VAbZrC/mfDU21exWEJabYMOtmuOgNiOnhsLfA0+x0Z4LG4uXzE9eGrZF92dzp+RRY4b2yqw0NiVOoP20pi2uCjkC62AUEW1587G7XNj1J8rDhKwU1QI5WeEgu7LmewZmIsouLi9ri/Wm7YJeGj65iZriw5RhSvTzPwpZMHJayuAO352h6+WtJYeNyTHcmyyEaG2sevsuFGvkKWqGuyOSAuwUC5YhR7SbCphpS09mOa7SLcj8g9B3JJt50jsyExu7SKQU8NiCCCQS3vEYf2ErRMISzBr6hZWPtMYH2mte6BOmNJmJztrcsCD2vmNh9XwqT2zYZR+VLbz+dYWPuH2VHy5uE/4odfiVe3s6+33VJbVwZkN9cqrI7EC/8AWvYeV7HWle9DJ0mExsS5cWSt2EiZW7AtJmt5GwHwqxbR2QJVmPDkzi7IQG8YEhUqNLE9fiOtI7q7FfaDTrfhLKOINM2ZRMbgG4tla4vY3udBUnvTgIsHlacSOZ7lcjKoAUhrE2uL5hyGtj7KzezJNUU/Y2BADyOUUx5iUkbI1gB6oOpY5iAo18NP4PneCitxAmQMFzG1mOZmPYk8+2WkosIMXiAseVGdgAWe4zHQXYLqSfLr76t2C3SxGFBklnMdrZpFIstmBF2BFl7gjW/uppLyLGdKkVCHZ9sQsQOVWWVVJ18JikU9uxFSvovh/CtlGqkX6jQi3sP3CnW9GKjcXXFcZw1x4Dy6jPrccuZ796hsDtWSBg8SRhitiCG09XQHLe3hB+PtpZJtGxaQhD/SsGfyYPuFK7iNlxOD09fEx6/o8lrf8RqbJJaWCS2kfDFu4jN9CeppXdWQDG4FL6pNGp9pxF/sI+FbvTGtNj/Zqj+c/oZ/1GqtyYhuGY7+EuGt+UFI+yrVh9HxA/8ABxH7FzVSdbnUga+f3a1PGPMayc2/jqKtuy8Qp2PJH9JcUHI/JaFFBv7VNVKXm3s+8VYtkoRgZ7gj5yI6i2hGh9lVye3/AKIx9xX2GtX3YQ+Zj7nA4of4VqiPz9/31fd3RdIR3wWLHwjFTycL8/0Vh3/H9lfaPSpbdu3yPaQuL2g/bGo3EzKoF768hYnl7OlSO7eDSTCY97HwcFlNrah2BGo7HUeYqUVtb4KNq6RTZBqfb+6nuH2W7qGvEFJOrTQqQL2PgkkU/G1/rq7bsei5cVCk5xRUPclViuVINrEl/Lt1qzbL9FEMLMTKJcwtaSJGA1vdQeRqryxRLSyM3k3BhxE8sxxwUM4zKIS+VuGvhZlk0JWzcutTezETDLbC4qFIQwyI+Fmcq3DKk5llUsWsxJI7W85jFbtuxbLNwwzByFjjF2CBdTbXQc+fLtR593oQLWOrA6MeYv8AvrlebItolljhJb8jJdpvcMmLgUgWNsHLzsMx1l6nvc8tTSibVkt/Tl9q4QDl+cxp3hN3olA9a/5zGlBu3D2bmT6560nq5Wb6eJdv6Iz+UJP/ALhJ/wDrRfuoVJ/6ORdm/vGu0erlN04v2jCINkqTd5X9hQMvwzGnH+jcba/KAD5gD6jak5NqZeaqRe2hIPwN706wuPR+49or0mmcKoSbdmSxCTwkG2ma3JbHQE8+d6Rg3QxCOr3Q5SG0PYg+ypVVH8Xo6Qj+BWWxqQ0wuwJc1jExB0BVgANfpEK3Typ3iN2l0+YxJawuRwyoHOwLKrE69VFGGFXsK6UIGhP11spyfcyMYrsMMVgrgBIMQPNka/2W+o0tszZWISTN8kmzCwLktdA4tcIqdiTc9qc/KpRpncDydh9QNKQ7QmUlllkBNrnMb6cqV21RqpPYTxO7gLTcVwWGYiOJlZ2z5bkra4Oijlaw5a0bd3doSRTDgtG4Z1R5JAhyspUGzWva2W3LxX18OVX+UZsxc5XY82ZEJPTVrBjXBtAaloBc88jvHfzNjU6lppMdOOq2QR2DkmaCWOV5TayxyR2N+uZgRpe/ke1SO3cHNwpDwGjIZlSNQzfNlrE+Em7XNyxvyuNDUgcRhH/C4eQ639YyC/fxt91SiwYadATdwLgB8+g0vlzHyHLtQ3VOQOnwRvodHDnKFJVZ0b1kIA4bk2DHmSHXS2lj3p/6X4c0WEbtn5+ax9qY4Q4RpTEqurrqPEeQtfL4jYA25gVJY3YYlUBnmZRqoZs6j82/L3Gn107E0WilbsjJicOdPw0Xf/ajvWv78L/MMX+ic/BCfuqiw7q8N1kRlJRldQynmrAgEksbeYsatm09qyT4bERPABJJEyDI4ZSShAvnCkC57GmeRN2ZoaRjCudLkcx9Idx7/dUi9rXvr2t996dybt4gamEj4Hr+Tek22cynKzKD530+A+y9UlOL4FUWhPEGKxsTfpzpbdnCKJ4JzMyhJkYqqggZZQ1r8QHW34p99SGDwGGWS5SSUAMMuYNqyEK1lTWzG/O3h1orJlHDWXEBdLKqJfwgAEX15afHqTUpST4HSfcLFAA+IkLprFOFGe5u0LhBlHU6C1VSWE2udDp95OnT39qt2F2XPI6pHNNfX1wo1AvqdLWUMT7O+lLQ7PwpjNsFI7Mc2czvZtPyQPv60sHGPLGlqfYq8e5+MkAdYGKsAQcyaggENq3XnU1icZnw0oMYjMaQxGzlrmFhGTry0K8tKfpxrLGpYxoSOGS55r6pOYMyW5Am3YUzGDuWCxLGpHjXI1h4lsQtyTy69uutiUlLYyKa3KTPJ4j7av8Aus/gw5/8rjR8IqlcLjSsSRrw0yxoAAgOoWxcsQbFm1ym9rnnzo2JmPyjCyKUbOmIRvEAEzxBFJN7C9uZsL0sp6tq/aHgqvcpOKLcRHUqcmti3XMCOncVNbmK3yXaK6FuGjWBHSUkmpfY260UcweWSNkUkFJDGQbgryVjci9wB1F9KT3V2csceJvIA80Jjy5WPzmYEBSNALBtPMa1n+zS+Aclqtcimxf5NThrmxsYl8QOeWNGIFiQVKg8gL27VKbSxuAZjIybQa5/q3mC8ugWSwGnYU0mxIGHOFBYHKUDDRgqyFsytmJ11HIDXna9VNNlGRwsqTjNYlnkRhcjmSpuQfK5+7NLvn+RrVGm4veHA8WVDh5ZGjKiQrGDYst1uc1+WnuNKxb54UDLkljUAAZ1CgWBbmW8re0gdap2K2c8m0Zoy1oiFdRqQXEMS3sCCTa451O7C3E4JkmlkXEZxdFdCFjvc3CszqeYHiGlqm0lFWx487D+H0kYAAlnddbaxyX+Cg/GnEfpI2a3/wBSB7Y5R9qUhhd1MNxUaXDwu4jAPhQKx6kxrGEv1v06VLJuxgufyLD3HXhx3/Vqd4/kaSY1/wBP9nf97j/x/urlScWxcMosuGjA15IvU3PLzrtbeP5E3MJEVuVh7AKXia3OhQr0DkHPFtSiyUKFKMG4nlRlmPnQoUAdJrlq7QoAKTQEtcoVgBuelvropjB6fX/lQoUAFEBGq6HuDY/EU8w22cSn9ZmHZ/F/iPi+BoUKxgPU3pOgkhB/Mcj6nDfaKWXeKIk5rxdiQT8chP2UKFK0hkyUwhLoZEdGXnmCsB/iIb6qPGDILgqwvbUdQfyvOhQqfkp2EVwg18KjvYAfYKax7uRfQ+b/ADT+9aFCtMEJN2ZCbrOALWsyE3B0INmFwRpypnNutiBpG6EcrAkadbaD2/51yhWgxjjdmYqMeNrC/ZSf1yOdM2nYkDNqDyAtbrzvrf7q7Qp1uIwpkubuGI0NrroToL6a6fC/lanbGNQ3P5tsjm5OtrjS2uut9elChQ+wLucR05hCyjTmRcDQKdRfp7uulFwjO5upJI5AMym+ayi5J8XXQgAA635ihS9hiRxkMizyMANGYkX0K8QsLjNYk3916SfaDaZczODa2gAsB1J7kdOnOuUKyQIX2jj+O6zcLh5VswDCx+iS1hcmw0ty0rRdl4gnCxNlAHDWwvc2C252HahQrnyFsXIZcURKAV5r5dO/iqTXEDtrXKFQOiUULZ/yfroUKFORo//Z"
    }
   },
   "cell_type": "markdown",
   "id": "bd0cede2",
   "metadata": {},
   "source": [
    "# UTILIZING MULTIPLE REGRESSION ANALYSIS TO PREDICT HOUSE PRICES IN KING COUNTY\n",
    "![king_county.jpg](attachment:king_county.jpg)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "452fa324",
   "metadata": {},
   "source": [
    "# Overview\n",
    "\n",
    "\"Upgrading older properties with renovations like kitchen and bathroom updates, adding bedrooms, and improving curb appeal increases their value by 20%.\" Source: [Mashvisor]. \n",
    "\n",
    "In numerous developed countries, housing prices have experienced significant growth over the past few decades. However, it is crucial to recognize that housing prices can deviate from their sustainable levels, leading to potential macroeconomic and financial stability concerns. Monitoring and assessing the sustainability of house prices is essential. This is according to the [IMF Working Paper of 2018 by Nan Geng](https://www.elibrary.imf.org/view/journals/001/2018/164/001.2018.issue-164-en.xml)."
   ]
  },
  {
   "cell_type": "markdown",
   "id": "06494bdb",
   "metadata": {},
   "source": [
    "## Business Understanding\n",
    "Some homeowners are eager to sell, but certain houses are undervalued due to wear and tear. Housing prices can fluctuate based on market trends and buyer preferences. Homeowners aim to increase their property value for higher selling prices, but they lack knowledge and insights on effective strategies to do so.\n",
    "\n",
    "Our analysis and modelling aimed to help homeowners looking to sell their houses make informed decisions by assessing how factors like home condition, size, renovations and more can impact their home's estimated value.\n",
    "\n",
    "### Objectives\n",
    "1. To find out whether the year the house was built and/or renovated affects the sale price of a house.\n",
    "2. To establish the effect of qualitative features of a house (grade, condition e.tc) on its sale price\n",
    "3. To establish the effect of quantitative features of a house (bedrooms, square footage) on its sale price."
   ]
  },
  {
   "cell_type": "markdown",
   "id": "0cd0f0fa",
   "metadata": {},
   "source": [
    "## Data Understanding\n",
    "The dataset provided (``kc_house_data.csv``) has information on the features of single-family house sales between 2014 and 2015. More information on this features is found in this link [Residential Glossary of Terms](https://info.kingcounty.gov/assessor/esales/Glossary.aspx?type=r#g). The file ``column_names.md`` contains column descriptions.\n",
    "\n",
    "- The analysis was based on King County data set.\n",
    "\n",
    "- It had a total of 21,597 records, containing 20 columns and 21,597 rows. \n",
    "\n",
    "- Timeframe of the data is 2014 to 2015. \n",
    "\n",
    "- Each row contains data of an  individual house, which is indexed by a unique house id. \n",
    "\n",
    "- The data has numerical and categorical variables.\n",
    "\n",
    "**Below is a list of the columns**:\n",
    "1.\tid: a notation for a house\n",
    "2.\tdate: Date house was sold\n",
    "3.\tprice: Price is prediction target\n",
    "4.\tbedrooms: Number of Bedrooms/House\n",
    "5.\tbathrooms: Number of bathrooms/bedrooms\n",
    "6.\tsqft_living: square footage of the home\n",
    "7.\tsqft_lot: square footage of the lot\n",
    "8.\tfloors: Total floors (levels) in house\n",
    "9.\twaterfront: House which has a view to a waterfront\n",
    "10.\tview: Has been viewed\n",
    "11.\tcondition: How good the condition is ( Overall ). 1 indicates worn out property and 5 excellent.\n",
    "12.\tgrade: Overall grade given to the housing unit, based on King County grading system. 1 poor ,13 excellent.\n",
    "13.\tsqft_above: Square footage of house apart from basement\n",
    "14.\tsqft_basement: Square footage of the basement\n",
    "15.\tyr_built: Year built\n",
    "16.\tyr_renovated: Year when house was renovated\n",
    "17.\tzipcode: zipcode\n",
    "18.\tlat: Latitude coordinate\n",
    "19.\tlong: Longitude coordinate\n",
    "20.\tsqft_living15: Living room area in 2015(implies-- some renovations) This might or might not have affected the lotsize area\n",
    "21.\tsqft_lot15: lotSize area in 2015(implies-- some renovations)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "75da0e23",
   "metadata": {},
   "source": [
    "## Modeling\n",
    "The model buidling began with checking the distribution of price. As per the diagram below, linear regression is the optimal method for this extensive dataset due to the non-normal distribution of the dependent variable, price.\n",
    "\n",
    "![price_dist](price_dist.png)\n",
    "\n",
    "### Collinearity\n",
    "\n",
    "We also checked for collinearity of features. \n",
    "\n",
    "![correlation](corr.jpg)\n",
    "\n",
    "It was noted that ``sqft_living`` is strongly correlated with two other predictor variables.\n",
    "\n",
    "![multi_coll](multi_coll.jpg)\n",
    "\n",
    "\n",
    "Six (6) models were built\n",
    "\n",
    "1. Base Model (Grade)\n",
    "2. All features excluding the dropped features\n",
    "3. The time factor (year built and year renovated).\n",
    "4. Qualitative features (categorical variables). \n",
    "5. Quantitative features (numerical variables).\n",
    "6. Quantitative features, adding a qualitative feature at a time. \n",
    "\n",
    "### Base Model\n",
    "- The model showed that high grade impacts positively on the price of a house. \n",
    "\n",
    "![base_model](base_model.jpg)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "9e51b8dd",
   "metadata": {},
   "source": [
    "### Ideal Model\n",
    "- out of the six models, our analysis found that the fifth model was the best fit in predicting house prices.\n",
    "- The model incorporated the numerical features and gave an **R squared of 0.84**. Approximately 84.3% of the variation in the dependent variable (price) can be explained by the numerical independent variables. \n",
    "- Other statistics of the model are: \n",
    "   - F-statistic 0f 2.188e+04 – indicating that the regression model is statistically significant\n",
    "   - p-values (below 0.05) – indicating statistical significance of the coefficients. "
   ]
  },
  {
   "cell_type": "markdown",
   "id": "2642ce68",
   "metadata": {},
   "source": [
    "## Regression Results\n",
    "- \n",
    "The model is a good fit since the training data and test data do not over fit or underfit\n",
    "\n",
    "![reg_results](reg_results.jpg)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "b8a0cfcb",
   "metadata": {},
   "source": [
    "## Conclusion\n",
    "- In conclusion, home sellers should take in the following:\n",
    "  - Consider increasing the space of the house, by increasing the number of floors, bathrooms & the size of basement & above ground area\n",
    "  - Highly graded houses fetch higher prices. Waterfront and views, also increase the value of houses. \n",
    "  - The newer the  house, the higher the price, similarly, the most recently renovated houses fetch higher prices. Therefore, sellers need to renovated their houses.\n",
    "   \n",
    "- Models that incorporate other features such as proximity to amenities, the nature of geographical features and the locality's weather conditions have an impact on a property's sale value.\n",
    "- Furthermore, it would be interesting to investigate whether certain months and seasons have an impact on the demand for homes."
   ]
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3 (ipykernel)",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.9.13"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
}
