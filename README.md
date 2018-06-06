# Final-Project

#T TEST
import pandas as pd
import numpy as np
df = pd.read_csv("Class Data - Sheet1.csv")
data2=df["Words recalled"].loc[df["Avg night sleep(hrs)"]>=7]
data1=df["Words recalled"].loc[df["Avg night sleep(hrs)"]<7]
def tvalue(groupA,groupB):
    XA=np.mean(groupA)
    XB=np.mean(groupB)
    SA=np.std(groupA)
    SB=np.std(groupB)
    nA=len(groupA)
    nB=len(groupB)
    tvalue=(abs(XA-XB))/(np.sqrt((SA**2/nA)+(SB**2/nB)))
    return(tvalue)
print(tvalue(data1,data2))

#SCATTER PLOT
words = words.dropna()
sleep = sleep.dropna()

np.mean(sleep)
np.mean(words)
plt.clf()

plt.scatter(sleep, words, s=50, color = 'blue', alpha = 0.7)
fit = np.polyfit(sleep, words, 1)
plt.plot(sleep, fit[0] * sleep + fit[1], color = 'red')
plt.xlabel("Hours of Sleep")
plt.ylabel("Numbers of Words")
plt.title("One Week Data")
plt.show()
plt.savefig('oneweekdata.png')

#BAR GRAPH
sleep7 = words.loc[sleep >= 7]
sleep6 = words.loc[sleep < 7]
plt.clf()
plt.bar(0, np.mean(sleep7), yerr = np.std(sleep7), capsize = 5, color = 'purple')
plt.bar(1, np.mean(sleep6), yerr = np.std(sleep6), capsize = 5, color = 'b')
plt.xticks([0,1], ["7+ hours of sleep", "Under 7 hours of sleep"])
plt.ylabel("Number of Words Correct")
plt.show()
plt.savefig('sleepcompare.png')

#HISTOGRAM
plt.hist(ns)
plt.axvline(7, linestyle='dashed')
plt.xlabel("Avg night sleep(hrs)")
plt.ylabel("Student")
plt.suptitle("Frequency of Hours of Sleep 1")
plt.show()
