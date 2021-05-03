FROM mileszim/rails-base-builder:3.0.0-alpine AS Builder
FROM mileszim/rails-base-final:3.0.0-alpine
USER app
CMD ["bundle", "exec", "puma", "-C", "config/puma.rb"]