import random
from faker import Faker
import re
fake = Faker("la")

regex = r"([0-9][0-9][/])+"

def with_date(frase):
    date = fake.date_object()
    date = f"{date.month:02}/{date.day:02}/{date.year:04}"
    return frase.replace(random.choice(frase.split()[:-1]), date)


if __name__ == "__main__":
    for i in range(random.randint(3, 20)):
        for i in range(random.randint(4, 20)):
            frase = fake.sentence()
            if random.random() < 0.25:
                frase = with_date(frase)

            if re.search(regex, str(frase)):
                string = re.search(regex, str(frase)).group(0)
                frase = re.sub( string, string[3] + string[4] + '/' + string[0] + string[1] + '/', frase)
