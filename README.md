# Python
# Ensure 'duration' is an integer
netflix_df['duration'] = pd.to_numeric(netflix_df['duration'], errors='coerce')

# Drop rows with NaN values in 'duration' column
netflix_df = netflix_df.dropna(subset=['duration'])

# Convert 'duration' to integer type
netflix_df['duration'] = netflix_df['duration'].astype(int)

# Frequent movies in 1990s
duration_df = netflix_df.loc[(netflix_df['release_year'].between(1990, 1999)) 
                             & (netflix_df['type'] == 'Movie')]

# Data frame information
netflix_df.info()
print(netflix_df.head(2))
netflix_df.shape

# Short action movies
movies_1990s = duration_df

filtered_df_short_action = movies_1990s.loc[(movies_1990s['type'] == 'Movie')  
                                            & (movies_1990s['genre'] == 'Action') 
                                            & (movies_1990s['duration'] < 90)]

short_movie_count = len(filtered_df_short_action)
print(f"Number of short action movies (less than 90 minutes) released in the 1990s: {short_movie_count}")
